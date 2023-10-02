# Coding Reflections and TDD Practice

## 1. Reflections

  ### 1.1 Shooting
  
    - Missed shot
    - Non-fatal hit
    - Bulletproof clothes/accessories
    - Non-lethal bullet
    - No bullet (?)
    - The man knew firstaid
  
  ### 1.2 Alien Toothbrush Instructions
  
    1. Pick up the toothbrush with the dominant hand.
    2. Hold it in the opposite end of the bristle.
    3. With the non-dominant hand, open the toothpaste tube by screwing the cap by turning it clockwise until it comes off.
    4. Squeeze a small amount of toothpaste onto the bristles of the toothbrush, just enough to cover the bristles.
    5. Wet the toothbrush under cold water to moisten the bristles.
    6. Lift the toothbrush to your mouth.
    7. Position the toothbrush at a slight angle to your teeth/gums.
    8. Start with the bottom teeth.
    9. Begin by brushing the outside of the teeth with gentle motions.
    10. Continue with the same motion on the inner surface of the teeth.
    11. Lastly, brush the chewing surfaces of the upper teeth with the same motion.
    12. Repeat the same process for your lower teeth.
    13. Don't forget to also brush your tongue to remove bacteria/smell.
    14. After brushing your teeth for about 2 minutes, spit out the excess toothpaste in the sink.
    15. Gently "whip" the toothbrush to remove any excess water.
    16. Rinse your mouth to remove any remaining toothpaste.
    17. Rinse your toothbrush under running water to wash off any leftover toothpaste.
    18. Place the cap back on the toothpaste tube and screw it on counterclockwise until it's sealed.
    19. Store the toothbrush and toothpaste in a clean, dry place.
    20. Do this regularly.

## 2. Two Katas

  ### 2.1 Temperarure converter

  Fahrenheit to celcius converter
```
import unittest

  # Step 2 - green, method implementation
  def fahrenheit_to_celsius(fahrenheit):
      celsius = (fahrenheit - 32) * 5.0/9.0
      return round(celsius, 2)

  # Step 1 - red, will fail initially
  class TestTemperatureConversion(unittest.TestCase):
      def test_fahrenheit_to_celsius_positive(self):
          self.assertEqual(fahrenheit_to_celsius(32), 0)

      def test_fahrenheit_to_celsius_negative(self):
          self.assertEqual(fahrenheit_to_celsius(-40), -40)

  if __name__ == '__main__':
      unittest.main()
  ```

Celcius to fahrenheit converter
```
import unittest

# Step 2 - green, method implementation
def celsius_to_fahrenheit(celsius):
    fahrenheit = (celsius * 9.0/5.0) + 32
    return round(fahrenheit, 2)

class TestTemperatureConversion(unittest.TestCase):

# Step 1 - red, will fail initially
    def test_celsius_to_fahrenheit_positive(self):
        self.assertEqual(celsius_to_fahrenheit(0), 32)

    def test_celsius_to_fahrenheit_negative(self):
        self.assertEqual(celsius_to_fahrenheit(-40), -40)
        
if __name__ == '__main__':
    unittest.main()
```

  ### 2.2 Roman numeral kata
```
import unittest
import random

# Step 2 - green, method implementation
def convert_to_roman(arabic):
    roman_numerals = {
        1: 'I',
        4: 'IV',
        5: 'V',
        9: 'IX',
        10: 'X',
        40: 'XL',
        50: 'L',
        90: 'XC',
        100: 'C',
        400: 'CD',
        500: 'D',
        900: 'CM',
        1000: 'M'
    }

    if arabic <= 0 or arabic > 3999:
        raise ValueError("Input out of range (1-3999): {}".format(arabic))

    result = ""
    for x in sorted(roman_numerals.keys(), reverse=True):
        while arabic >= x:
            result += roman_numerals[x]
            arabic -= x

    return result

# Step 1 - red, will fail initially
class TestRomanNumeralConversion(unittest.TestCase):
    def test_convert_to_roman(self):
        arabic = random.randint(1, 3999)
        roman = convert_to_roman(arabic)
        self.assertEqual(convert_to_roman(arabic), roman)

if __name__ == '__main__':
    unittest.main()
```
  

## 3. Give your thoughts on TDD

### What was the positive and good about using TDD?
The positive was that the code design was more robust (and actually worked as intented). It's very nice that tests actually gives       information wether the code works or doesn't work (meaning the actual/expected values). In the code I made, I thought it was nice that when the test failed, it said what the actual value was and what the expected value was.

### What was annoying or difficult?
The whole red-green-refactor thought-process was a little hard to understand in the beginning. It felt a little weird to make the code   fail at first, and then fix it. 
Also due to our very limited experience with testing, it was quite difficult to get the idea of how the test should be written, and then actually write it.

### What surprised you?
How easy and stong tests actually is to implement once you'd get the hang of it. The idea of testing seems really nice and I've always thought that when you're in the "real" world, tests seems kind of redundant - but I can conclude that it is not the case!

### Did TDD help you write some tests you wouldn’t otherwise have thought of?
Well kind of, yes. In the Roman Numeral Kata, I did things alot different than in the temperature converter. Intially I just created very static tests, that only tested if 5 == 'V' and so on.
However, I wanted to make it more dynamic, meaning that I wanted to be able to test *every* number from 1-3999. I'm not quite sure if I implemetned it correctly with the red-green-refactor/tdd principles (it's mostly the reactoring part I'm unsure about), but I gave it our best shot!
