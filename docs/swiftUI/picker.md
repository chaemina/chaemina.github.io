---
layout: default
title: Picker
parent: Swift UI
nav_order: 15
---


# Picker
{: .no_toc }


## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Picker

 `Form - section - picker`

```swift
Form{
     Section{
         Picker(selection: $selectedIndex,label: Text("기종 선택")){
              ForEach(0 ..< typeOfPhone.count, id: \.self){ index in
                     Text(typeOfPhone[index])}
              } // : picker
              .pickerStyle(.wheel)
           } // : section
}
```

배열을 ForEach문으로 돌면서, swift에서 지원해주는 pickerStyle로 선택 가능한 메뉴를 만든다. 

## PickerStyle

### automatic (menu)
ios 17에서 automatic은 menu와 같다. 

<img src="../../../assets/images/picker-auto.png" alt="assert Image" aria-label="assert Image" width="300" height="500">

### inline

<img src="../../../assets/images/picker-inline.png" alt="assert Image" aria-label="assert Image" width="300" height="500">

### segmented

<img src="../../../assets/images/picker-segmented.png" alt="assert Image" aria-label="assert Image" width="300" height="500">

### wheel

<img src="../../../assets/images/picker-wheel.png" alt="assert Image" aria-label="assert Image" width="300" height="500">