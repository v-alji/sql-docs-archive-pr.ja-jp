---
title: '[Foreach ループエディター] ([変数のマッピング] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd37c8c6c00f18d8b5493a058239cc880ecc1f5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743378"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a><span data-ttu-id="579eb-102">[ForEach ループ エディター] ([変数のマッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="579eb-102">Foreach Loop Editor (Variable Mappings Page)</span></span>
  <span data-ttu-id="579eb-103">**[Foreach ループ エディター]** ダイアログ ボックスの **[変数のマッピング]** ページを使用すると、コレクションの値に変数をマップできます。</span><span class="sxs-lookup"><span data-stu-id="579eb-103">Use the **Variables Mappings** page of the **Foreach Loop Editor** dialog box to map variables to the collection value.</span></span> <span data-ttu-id="579eb-104">変数の値は、ループの各反復処理でコレクションの値を使用して更新されます。</span><span class="sxs-lookup"><span data-stu-id="579eb-104">The value of the variable is updated with the collection values on each iteration of the loop.</span></span>  
  
 <span data-ttu-id="579eb-105">Integration Services パッケージでの Foreach Loop コンテナーの使用方法の詳細については、「 [Foreach Loop Container](control-flow/foreach-loop-container.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="579eb-105">To learn about how to use the Foreach Loop container in an Integration Services package,  see [Foreach Loop Container](control-flow/foreach-loop-container.md) .</span></span> <span data-ttu-id="579eb-106">構成方法の詳細については、「 [Foreach ループ コンテナーを構成する](../../2014/integration-services/configure-a-foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="579eb-106">To learn about how to configure it, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="579eb-107">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] チュートリアルの「簡単な ETL パッケージの作成」には、Foreach ループの追加および構成について説明するレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="579eb-107">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial, Creating a Simple ETL Package Tutorial, includes a lesson that teaches you to add and configure a Foreach Loop.</span></span>  
  
## <a name="options"></a><span data-ttu-id="579eb-108">Options</span><span class="sxs-lookup"><span data-stu-id="579eb-108">Options</span></span>  
 <span data-ttu-id="579eb-109">**変数**</span><span class="sxs-lookup"><span data-stu-id="579eb-109">**Variable**</span></span>  
 <span data-ttu-id="579eb-110">既存の変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="579eb-110">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="579eb-111">変数をマップした後、新しい行が **[変数]** リストに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="579eb-111">After you map a variable, a new row is automatically added to the **Variable** list.</span></span>  
  
 <span data-ttu-id="579eb-112">**関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="579eb-112">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="579eb-113">**Index**</span><span class="sxs-lookup"><span data-stu-id="579eb-113">**Index**</span></span>  
 <span data-ttu-id="579eb-114">Foreach Item 列挙子を使用する場合、変数にマップするコレクションの値に列のインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="579eb-114">If using the Foreach Item enumerator, specify the index of the column in the collection value to map to the variable.</span></span> <span data-ttu-id="579eb-115">他の列挙子の型では、インデックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="579eb-115">For other enumerator types, the index is read-only.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="579eb-116">インデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="579eb-116">The index is 0-based.</span></span>  
  
 <span data-ttu-id="579eb-117">**関連トピック**: [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する方法](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span><span class="sxs-lookup"><span data-stu-id="579eb-117">**Related Topics**: [Loop through Excel Files and Tables by Using a Foreach Loop Container](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)</span></span>  
  
 <span data-ttu-id="579eb-118">**削除**</span><span class="sxs-lookup"><span data-stu-id="579eb-118">**Delete**</span></span>  
 <span data-ttu-id="579eb-119">変数を選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="579eb-119">Select a variable, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579eb-120">参照</span><span class="sxs-lookup"><span data-stu-id="579eb-120">See Also</span></span>  
 <span data-ttu-id="579eb-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="579eb-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="579eb-122">[Foreach ループエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="579eb-122">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="579eb-123">[Foreach ループエディター &#40;コレクションページ&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span><span class="sxs-lookup"><span data-stu-id="579eb-123">[Foreach Loop Editor &#40;Collection Page&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md) </span></span>  
 <span data-ttu-id="579eb-124">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="579eb-124">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="579eb-125">For ループ コンテナー</span><span class="sxs-lookup"><span data-stu-id="579eb-125">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
