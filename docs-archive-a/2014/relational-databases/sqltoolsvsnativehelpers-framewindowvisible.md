---
title: FrameWindowVisible | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 414f1a03ea87f6cc6b0916a0122ca2a66d5855a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743137"
---
# <a name="framewindowvisible"></a><span data-ttu-id="bb563-102">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="bb563-102">FrameWindowVisible</span></span>
  <span data-ttu-id="bb563-103">指定されたウィンドウ フレームを表示するかどうかを示すプロパティです。</span><span class="sxs-lookup"><span data-stu-id="bb563-103">Property that specifies whether a given window frame is visible.</span></span> <span data-ttu-id="bb563-104">ヘルパー メソッドは、マネージド コードから使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb563-104">The helper method is used from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb563-105">構文</span><span class="sxs-lookup"><span data-stu-id="bb563-105">Syntax</span></span>  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb563-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb563-106">Parameters</span></span>  
 <span data-ttu-id="bb563-107">*frame*</span><span class="sxs-lookup"><span data-stu-id="bb563-107">*frame*</span></span>  
  
 <span data-ttu-id="bb563-108">Visual Studio WindowFrame への IVsWindowFrame\* ポインターです。</span><span class="sxs-lookup"><span data-stu-id="bb563-108">IVsWindowFrame\* pointer to a Visual Studio WindowFrame.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="bb563-109">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="bb563-109">Property Value/Return Value</span></span>  
 <span data-ttu-id="bb563-110">*frame* で指定したウィンドウ フレームを表示するかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="bb563-110">A Boolean value that specifies whether the window frame specified by *frame* is visible.</span></span>  
  

<!-- Necessary temporarily. GeneMi, 2018-05-01.
     But 'release-sql2014-migration' should win the Conflict Resolution later in May, because this will then be a good link!
## See Also  
 [SqlToolsVSNativeHelpers](sqltoolsvsnativehelpers.md)  
-->
  
  
