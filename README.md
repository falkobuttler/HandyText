TextStyle
--------------

Purpose
--------------
TextStyle is a helper library that allows to create and manage text styles in clear declarative manner.

Problem solved
--------------

Work on UI tasks is full of repetition when it goes about defining text appearance. You have to refer to mockups all the time, or to search and copy elements of same appearance. Both ways leave many ways for errors, and both make late changes in design quite painful. Amount of work for changing a font in typical elements is proportional to project's size.
The alternative way is in avoiding the use of IB for defining text appearance, but handling it in code. 


Supported OS & SDK Versions
-----------------------------

Swift 2.2
* Supported build target - iOS 9.0 (Xcode 7)

Installation
--------------

Copy contents of TextStyle directory to your project. Declare own text styles as static functions or properties of TextStyle struct.

Version 1.0

- Release version.

Usage
--------------

First, let's define some text styles:

extension TextStyle {
  static var plainText: TextStyle {
    return TextStyle(font: .Avenir)
  }
}

The Font is only required parameter for creating a brand new style, all other params are set do defaults. Instead of copying instances and modifying properties the library proposes more declarative 'cascade' style. Think you need a style for headers based on plain text:

  static var header1: TextStyle {
    return plainText.withSizeMultipliedBy(1.4).uppercase().bold()
  }

In text there also will be clickable links. Links will have same font and size as plain text, but italic, blue and underlined:

  static func url(link: String) -> TextStyle {
    return plainText.withForegroundColor(.blueColor()).italic().withUnderline(.StyleSingle).withLink(link)
  }

It's remarkable that styles are chained, in other words based on each other. Changing basic style font to .Georgia makes all style scheme look different, but still well aligned.

Attributed strings
----------------

The costs of using text styles is switching to attributed text, which is supported by the most of UIKit classes.
self.testLabel.attributedText = "Hello World".withStyle(.plainText)



License
----------------

    The MIT License (MIT)

    Copyright © 2016 Aleksey Chernish

    Permission is hereby granted free of charge to any person obtaining a copy of this software and associated documentation files (the "Software") to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.

