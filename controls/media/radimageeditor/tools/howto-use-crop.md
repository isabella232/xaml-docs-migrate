---
title: Cropping
page_title: Cropping
description: Cropping
slug: radimageeditor-tools-crop
tags: cropping
published: True
position: 1
---

# Cropping



__CropTool__ is one of the tool that come out-of-the-box with __RadImageEditor__ and gives the opportunity to crop a given area from an image. The tool provides some customization options that are explained in detail in this topic.
      

* [InitialSize](#initialsize)

* [FixedSize](#fixedsize)

* [AspectRatio](#aspectratio)

When the tool is invoked a rectangle is shown over the image. It is called crop adorner and visualizes the part of the images that is going to be cropped when the tool is invoked.
      

Crop Adorner![Rad Image Editor How To Use Crop 01](images/RadImageEditor_HowTo_Use_Crop_01.png)

The tool is located in the Telerik.Windows.Media.Imaging.Tools namespace and can be defined in XAML as demonstrated in **Example 1**.
      

#### __[XAML] Example 1: Create CropTool__

{{region xaml-radimageeditor-tools-crop_0}}
	<tools:CropTool />
{{endregion}}



## InitialSize

The __InitialSize__ property is of type Size and determines the initial size of the crop adorner. Unless explicitly set, the rectangle has width and height equal to 80% of the width and height of the image that is shown in the control.
        

__Example 2__ demonstrates how to set the initial size of the tool in XAML and in code.
        

#### __[XAML] Example 2: Set initial size__

{{region xaml-radimageeditor-tools-crop_1}}
	<tools:CropTool InitialSize="150,150" />
{{endregion}}



#### __[C#] Example 2: Set initial size__

{{region cs-radimageeditor-tools-crop_2}}
	CropTool cropTool = new CropTool();
	cropTool.InitialSize = new Size(150, 150);
{{endregion}}



#### __[VB.NET] Example 2: Set initial size__

{{region vb-radimageeditor-tools-crop_3}}
	Dim cropTool As New CropTool()
	cropTool.InitialSize = New Size(150, 150)
{{endregion}}



## FixedSize

The __FixedSize__ property is of type Size and specifies the only size that is allowed for the Crop tool. This means that the crop adorner is shown with those dimensions and resizing it is not possible.
        

__Example 3__ shows how to set fixed size in XAML and in code.
        

#### __[XAML] Example 3: Set fixed size__

{{region xaml-radimageeditor-tools-crop_4}}
	<tools:CropTool FixedSize="200,100" />
{{endregion}}



#### __[C#] Example 3: Set fixed size__

{{region cs-radimageeditor-tools-crop_5}}
	CropTool cropTool = new CropTool();
	cropTool.FixedSize = new Size(200, 100);
{{endregion}}



#### __[VB.NET] Example 3: Set fixed size__

{{region vb-radimageeditor-tools-crop_6}}
	Dim cropTool As New CropTool()
	cropTool.FixedSize = New Size(200, 100)
{{endregion}}



>If the image shown in RadImageEditor has smaller dimensions than the ones set for the tool's initial or fixed size, the crop adorner gets limited to the boundaries of the image. For example, if the image's size is (200,300) and you set fixed size to the crop tool (300,50), the crop rectangle will be shown with size (200,50).
          

## AspectRatio

The __AspectRatio__ property of the crop tool determines whether the width and height of the crop adorner are in linear dependence. The value can be a positive decimal number and specifying it "locks" the ratio between the width and height of the crop rectangle.
        

The calculated ratio value corresponds to the width of the adorner divided by its height. This means that if you want a crop rectangle that has a width 2 times smaller than its height, you should set value 0.5 to the AspectRatio. __Example 3__ shows how this can be done in XAML and in code behind.
        

#### __[XAML] Example 3: Set fixed aspect ratio__

{{region xaml-radimageeditor-tools-crop_7}}
	<tools:CropTool AspectRatio="0.5"/>
{{endregion}}



#### __[C#] Example 3: Set fixed aspect ratio__

{{region cs-radimageeditor-tools-crop_8}}
	CropTool cropTool = new CropTool();
	cropTool.AspectRatio = 0.5;
{{endregion}}



#### __[VB.NET] Example 3: Set fixed aspect ratio__

{{region vb-radimageeditor-tools-crop_9}}
	Dim cropTool As New CropTool()
	cropTool.AspectRatio = 0.5
{{endregion}}



>tipYou can crop an image with fixed ration between the width and height without setting the FixedRatio property. Just press and hold the __Shift__ key while dragging the crop adorner.
          

## See Also

* [Commands and Tools]({%slug radimageeditor-features-commands-and-tools%})
* [Drawing]({%slug radimageeditor-tools-drawing%})
* [Shape Tool]({%slug radimageeditor-tools-shape-tool%})