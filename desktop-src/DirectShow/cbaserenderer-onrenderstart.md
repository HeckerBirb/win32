---
Description: The OnRenderStart method is called when rendering is about to start.
ms.assetid: 46af24cf-9075-4ebc-a49b-85f8f0c3da6f
title: CBaseRenderer.OnRenderStart method
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# CBaseRenderer.OnRenderStart method

The `OnRenderStart` method is called when rendering is about to start.

## Syntax


```C++
virtual void OnRenderStart(
   IMediaSample *pMediaSample
);
```



## Parameters

<dl> <dt>

*pMediaSample* 
</dt> <dd>

Pointer to the sample's [**IMediaSample**](/windows/desktop/api/Strmif/nn-strmif-imediasample) interface.

</dd> </dl>

## Return value

This method does not return a value.

## Remarks

The [**CBaseRenderer::Render**](cbaserenderer-render.md) method calls this method. It does nothing in the base class, but the derived class can override it; for example, to collect quality-control data.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Renbase.h (include Streams.h)</dt> </dl>                                                                                   |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CBaseRenderer Class**](cbaserenderer.md)
</dt> </dl>

 

 



