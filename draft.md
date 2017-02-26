# Android Resources Refactoring
- DroidKaigi2017 3/9(Thu)
- @konifar / Quipper
- [konifar_image]
-

<!--
- Is it okay to start? Okay, let's get started!
Thank you for coming this session.
I'm Yusuke Konishi, my GitHub and Twitter name is @konifar which icon is Draemon as you can see.
I'm working at Quipper Ltd., and sometimes create private project.
My recent project is this DroidKaigi official app.
-->

---

# DroidKaigi 2017 app
- [app_images]
- URL

<!--
This app is totally OSS on GitHub, and has many many contributors.
Are there any contributors in this room? Please raise your hand!
- Oh no, There is no body in this room, but I appreciate all contributors so much!
- Thanks you so much! I wanna talk you after this session.

In fact, this app is the sample of this session.
If you don't mind, please watch out the GitHub repository.
-->

# Why I talk about this
- [design_change_images]
- June, October, February

<!--
Then, let's get started today's main theme.
This session title is "Android Resources Refactoring".
Why I want to talk this session?
I joined to Quipper Ltd at June last year, and I had changed the design 2 times for 8 months.
It was a little hard task because the resources were lawless.
You know, Text and margin size are written directly in layout,
There are so many colors and lawless styles. It looked like nightmare.

It was hard tasks. but after some try and errors, I found my best practice to manage resources.
So today, I want to talk about the best practice and the practical way to refactor the resources.
-->

---

# themes & styles depend on other resources
- colors
```
<color name="text_grey5">#323232</color>
```

- dimens
```
<dimen name="text_caption">12dp</dimen>
<item name="text_spacing_multiplier_1.3" format="float" type="dimen">1.3</item>
```

- styles
```
<style name="TextCaption">
  <item name="android:textSize">@dimen/text_caption</item>
  <item name="android:textColor">@color/text_grey5</item>
  <item name="android:lineSpacingMultiplier">@dimen/text_spacing_multiplier_1.3</item>
</style>
```

<!--
As you know, the almost resources are in res/values directory.
In fact, there is dependencies between each resources.
As you can see, colors and dimens are defined in styles.
In other words, themes and styles are combination of the other resources.

So if you want to refactor the resources, it's better to modify colors and dimens at first.
-->

---

# colors

<!--
First, I'll talk about colors.
On Android, we can define colors to give a feeling of unity.
-->

---

# colors principle
Divide 2 files.

## colors_palette.xml
- Defined as just color palette.
```
<color name="">#606060</color>
```
## colors.xml
- Defined colors by each components.
```
<color name="text_grey5">@color/grey5</color>
```

<!--
There are many way to define colors.
I recommend to divide 2 files, colors_palette.xml and colors.xml.
colors_palette.xml defines the colors which are used in your App.
colors.xml is not mandatory. this defines the colors for each components. such as text and button.
-->

---

# colors_palette.xml
- [color_schemes]
- [colors_palette.xml]

<!--
Our designers created color scheme.
I created colors.xml from it.
I think the naming rule is the most important.
In my opinion, the color's name should be decided with the designers.
Because it's easier to understand when the design are given.
It becomes common color palette between engineers and designers.

If there is no designers in your company, I think any names can be okay.
Actually, in DroidKaigi app, I use the simple color name such as `blue`, `red` and `green`.
-->

---

# colors.xml
- [colors.xml]
- [image_grey3_color]


<!--
Why I need second color.xml?
Because sometimes same colors have different meanings.
As you can see, this text and button text color are same color.
But this button text color might be changed in the future.
If we use the color from colors_palette.xml, it's hard to change only button color.
So I define colors for each components.
-->

---

# How to refactor colors at first?
1. Create colors_new.xml
2. Grep old color name and replace it to new one.
3. Grep color code which is written directly and replace it to new color name.
4. After replacing all colors, remove old colors.xml
5. Rename colors_new.xml to colors.xml

<!--
When we start to refactor colors in my app, there might be old colors.
I think it's better to create other file like colors_new.xml and replace old colors to new colors one by one.
Grep and replace, Grep and replace. Sometimes there is strange colors which is not specified in new colors.
When I found it, I ask to the designers how I should do this strange colors. Most of them was replaced to similar color. In that sense, this is not exactly refactoring because I changed the design.
After replaced all colors, I removed old colors xml file and renamed new colors xml file.
-->

---

# dimens

<!--
After refactoring colors, next target is dimens.
As I explained before, colors and dimens are primitive resources.
-->

---

# dimens principle
Divide 2 files.

## dimens_base.xml
- Defined primitive dimens
```
<color name="space_8dp">8dp</color>
```
## dimens.xml
- Defined dimens for specific pages
```
<color name="text_grey5">@color/grey5</color>
```

<!--
As same with colors, I recommend to divide 2 files.
dimens_base defines basic dimens such as margin, text, list.
In other words, these dimens are for common component, not for specific pages.

On the other hand, dimens.xml is for specific pages
-->

---

# Example
- [Quiz page]
```
This page is specific.
```

---

# themes & styles

---



---

---
