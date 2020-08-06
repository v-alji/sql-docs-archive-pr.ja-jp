---
title: SqlToolsVSNativeHelpers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84f8a3a3408b68cb8c389b05b417f391a1f86c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743133"
---
# <a name="sqltoolsvsnativehelpers"></a><span data-ttu-id="7dee1-102">SqlToolsVSNativeHelpers</span><span class="sxs-lookup"><span data-stu-id="7dee1-102">SqlToolsVSNativeHelpers</span></span>
  <span data-ttu-id="7dee1-103">Visual Studio の SQL Server 機能をサポートするライブラリです。</span><span class="sxs-lookup"><span data-stu-id="7dee1-103">Library that supports SQL Server functionality in Visual Studio.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dee1-104">構文</span><span class="sxs-lookup"><span data-stu-id="7dee1-104">Syntax</span></span>  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a><span data-ttu-id="7dee1-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="7dee1-105">Return Value</span></span>  
 <span data-ttu-id="7dee1-106">ブール値。DLL エントリ ポイントが適切に初期化されている場合は `True`、それ以外の場合は `False` です。</span><span class="sxs-lookup"><span data-stu-id="7dee1-106">A Boolean value, `True` if the DLL entry point initialized properly, otherwise `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dee1-107">参照</span><span class="sxs-lookup"><span data-stu-id="7dee1-107">See Also</span></span>  
 [<span data-ttu-id="7dee1-108">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="7dee1-108">FrameWindowVisible</span></span>](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
