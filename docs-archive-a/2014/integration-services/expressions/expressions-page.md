---
title: '[式] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ba4e73ea495456e8f9e452108ab09106a65543ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640178"
---
# <a name="expressions-page"></a><span data-ttu-id="a5780-102">[式] ページ</span><span class="sxs-lookup"><span data-stu-id="a5780-102">Expressions Page</span></span>
  <span data-ttu-id="a5780-103">**[式]** ページを使用すると、プロパティ式を編集でき、 **[プロパティ式エディター]** ダイアログ ボックスや **[式ビルダー]** ダイアログ ボックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a5780-103">Use the **Expressions** page to edit property expressions and to access the **Property Expressions Editor** and **Property Expression Builder** dialog boxes.</span></span>  
  
 <span data-ttu-id="a5780-104">プロパティ式は、パッケージが実行されたときに、プロパティの値を更新します。</span><span class="sxs-lookup"><span data-stu-id="a5780-104">Property expressions update the values of properties when the package is run.</span></span> <span data-ttu-id="a5780-105">プロパティ式は、パッケージ、タスク、コンテナー、接続マネージャーに加えて、一部のデータ フロー コンポーネントのプロパティでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5780-105">Property expressions can be used with the properties of packages, tasks, containers, connection managers, as well as some data flow components.</span></span> <span data-ttu-id="a5780-106">式が評価されると、その結果が、パッケージおよびパッケージ オブジェクトの構成時にプロパティに設定した値の代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="a5780-106">The expressions are evaluated and their results are used instead of the values to which you set the properties when you configured the package and package objects.</span></span> <span data-ttu-id="a5780-107">式には、変数と、式の言語で提供されている関数および演算子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a5780-107">The expressions can include variables and the functions and operators that the expression language provides.</span></span> <span data-ttu-id="a5780-108">たとえば、文字列 "Weather forecast for " を含む変数の値と、GETDATE() 関数によって返される結果を連結して、文字列 "Weather forecast for 4/5/2006" を作成することにより、メール送信タスクの件名行を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="a5780-108">For example, you can generate the subject line for the Send Mail task by concatenating the value of a variable that contains the string "Weather forecast for " and the return results of the GETDATE() function to make the string "Weather forecast for 4/5/2006".</span></span>  
  
 <span data-ttu-id="a5780-109">式の作成とプロパティ式の使用の詳細については、「 [Integration Services &#40;SSIS&#41; 式](integration-services-ssis-expressions.md) ダイアログ ボックスや [パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5780-109">To learn more about writing expressions and using property expressions, see [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) and [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a5780-110">オプション</span><span class="sxs-lookup"><span data-stu-id="a5780-110">Options</span></span>  
 <span data-ttu-id="a5780-111">**式 (...)**</span><span class="sxs-lookup"><span data-stu-id="a5780-111">**Expressions (...)**</span></span>  
 <span data-ttu-id="a5780-112">[...] をクリックすると、 **[プロパティ式エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5780-112">Click the ellipsis to open the **Property Expressions Editor** dialog box.</span></span> <span data-ttu-id="a5780-113">詳細については、「 [プロパティ式エディター](property-expressions-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5780-113">For more information, see [Property Expressions Editor](property-expressions-editor.md).</span></span>  
  
 **\<property name>**  
 <span data-ttu-id="a5780-114">[...] をクリックすると、 **[式ビルダー]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5780-114">Click the ellipsis to open the **Expression Builder** dialog box.</span></span> <span data-ttu-id="a5780-115">詳細については、「 [式ビルダー](expression-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5780-115">For more information, see [Expression Builder](expression-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5780-116">参照</span><span class="sxs-lookup"><span data-stu-id="a5780-116">See Also</span></span>  
 <span data-ttu-id="a5780-117">[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="a5780-117">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="a5780-118">[システム変数](../system-variables.md) </span><span class="sxs-lookup"><span data-stu-id="a5780-118">[System Variables](../system-variables.md) </span></span>  
 [<span data-ttu-id="a5780-119">Integration Services &#40;SSIS&#41; 式</span><span class="sxs-lookup"><span data-stu-id="a5780-119">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
