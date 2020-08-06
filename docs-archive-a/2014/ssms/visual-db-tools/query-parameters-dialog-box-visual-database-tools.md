---
title: '[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 76052876ad2899fc959aa7fc49f4299e08bac713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713682"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a><span data-ttu-id="dd5bc-102">[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dd5bc-102">Query Parameters Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="dd5bc-103">このダイアログ ボックスを使用すると、クエリに定義されたパラメーターの値を入力できます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-103">This dialog allows you to enter values for the parameters defined in the query.</span></span> <span data-ttu-id="dd5bc-104">このダイアログ ボックスは、エンド ユーザーが値を入力する必要があるパラメーターを含むクエリを実行するときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-104">This dialog box appears when you execute a query that contains parameters that require end-user input at run time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd5bc-105">オプション</span><span class="sxs-lookup"><span data-stu-id="dd5bc-105">Options</span></span>  
 <span data-ttu-id="dd5bc-106">**Name**</span><span class="sxs-lookup"><span data-stu-id="dd5bc-106">**Name**</span></span>  
 <span data-ttu-id="dd5bc-107">実行するクエリに対して定義されているパラメーターを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-107">Lists the parameters defined for the query being executed.</span></span> <span data-ttu-id="dd5bc-108">クエリに名前付きのパラメーターが含まれる場合は、名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-108">If the query contains named parameters, the names appear in the list.</span></span> <span data-ttu-id="dd5bc-109">クエリに名前のないパラメーターが含まれる場合、クエリ内のパラメーターごとに、システム定義のパラメーター名が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-109">If the query contains unnamed parameters, system-defined parameter names are listed for each parameter in the query.</span></span>  
  
 <span data-ttu-id="dd5bc-110">**Value**</span><span class="sxs-lookup"><span data-stu-id="dd5bc-110">**Value**</span></span>  
 <span data-ttu-id="dd5bc-111">**[名前]** に一覧表示された各パラメーターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-111">Enter the value for each parameter listed under **Name**.</span></span> <span data-ttu-id="dd5bc-112">最後に使用した値が既定の値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-112">The value used most recently appears as the default parameter value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd5bc-113">例</span><span class="sxs-lookup"><span data-stu-id="dd5bc-113">Example</span></span>  
 <span data-ttu-id="dd5bc-114">SQL ペインに入力された次のクエリが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで実行されると、[クエリ パラメーター] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="dd5bc-114">The following query in the SQL Pane, opens the Query Parameters dialog box when executed in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd5bc-115">参照</span><span class="sxs-lookup"><span data-stu-id="dd5bc-115">See Also</span></span>  
 [<span data-ttu-id="dd5bc-116">パラメーターを使用したクエリ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dd5bc-116">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
