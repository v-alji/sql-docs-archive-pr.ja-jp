---
title: エラー処理 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643580"
---
# <a name="error-handling-mdx"></a><span data-ttu-id="b4041-102">エラー処理 (MDX)</span><span class="sxs-lookup"><span data-stu-id="b4041-102">Error Handling (MDX)</span></span>
  <span data-ttu-id="b4041-103">各キューブでは、多次元式 (MDX) スクリプト内のエラーの処理方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="b4041-103">Each cube can control how errors within a Multidimensional Expressions (MDX) script are handled.</span></span> <span data-ttu-id="b4041-104">エラー処理は `ScriptErrorHandlingMode` 列挙子を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="b4041-104">Error handling is done through the `ScriptErrorHandlingMode` enumerator.</span></span> <span data-ttu-id="b4041-105">この列挙子は、以下のいずれかの値をとります。</span><span class="sxs-lookup"><span data-stu-id="b4041-105">The possible values for this enumerator are:</span></span>  
  
 `IgnoreNone`  
 <span data-ttu-id="b4041-106">によって、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MDX スクリプトでエラーが検出されると、サーバーでエラーが発生し [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b4041-106">Causes the server to raise an error when [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] finds any error in the MDX script.</span></span>  
  
 `IgnoreAll`  
 <span data-ttu-id="b4041-107">サーバーは、MDX スクリプト内のエラー (構文エラー、名前の解決エラーなど) を含むすべてのコマンドを無視します。</span><span class="sxs-lookup"><span data-stu-id="b4041-107">Causes the server to ignore all commands in the MDX script that contain an error, including syntax errors, name resolution errors, and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4041-108">参照</span><span class="sxs-lookup"><span data-stu-id="b4041-108">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
