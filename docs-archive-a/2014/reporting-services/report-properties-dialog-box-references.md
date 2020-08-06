---
title: '[参照] ([レポートのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b28ea0865d37bdc56054d6b23dc8c82d9279b08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717384"
---
# <a name="report-properties-dialog-box-references"></a><span data-ttu-id="a6fc0-102">[参照] ([レポートのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="a6fc0-102">Report Properties Dialog Box, References</span></span>
  <span data-ttu-id="a6fc0-103">**[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6fc0-104">Options</span><span class="sxs-lookup"><span data-stu-id="a6fc0-104">Options</span></span>  
 <span data-ttu-id="a6fc0-105">**[アセンブリの追加または削除]**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-105">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="a6fc0-106">レポートで参照されるアセンブリを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-106">Lists the assemblies that the report references.</span></span> <span data-ttu-id="a6fc0-107">アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-107">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="a6fc0-108">参照の名前は、 **\<CodeModule>** レポート定義言語 (.rdl) ファイルのタグの内容と正確に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-108">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="a6fc0-109">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-109">**Add**</span></span>  
 <span data-ttu-id="a6fc0-110">アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-110">Click to add an assembly.</span></span> <span data-ttu-id="a6fc0-111">省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なアセンブリを選択します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-111">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="a6fc0-112">**削除**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-112">**Delete**</span></span>  
 <span data-ttu-id="a6fc0-113">アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-113">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="a6fc0-114">**[クラスの追加または削除]**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-114">**Add or remove classes**</span></span>  
 <span data-ttu-id="a6fc0-115">レポートで使用されるクラスのインスタンスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-115">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="a6fc0-116">クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-116">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="a6fc0-117">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-117">**Add**</span></span>  
 <span data-ttu-id="a6fc0-118">クラスの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-118">Click to add a class reference.</span></span> <span data-ttu-id="a6fc0-119">省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なクラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-119">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="a6fc0-120">**削除**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-120">**Delete**</span></span>  
 <span data-ttu-id="a6fc0-121">クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-121">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="a6fc0-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-122">**Up**</span></span>  
 <span data-ttu-id="a6fc0-123">依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-123">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="a6fc0-124">**[下へ]**</span><span class="sxs-lookup"><span data-stu-id="a6fc0-124">**Down**</span></span>  
 <span data-ttu-id="a6fc0-125">依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。</span><span class="sxs-lookup"><span data-stu-id="a6fc0-125">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fc0-126">参照</span><span class="sxs-lookup"><span data-stu-id="a6fc0-126">See Also</span></span>  
 <span data-ttu-id="a6fc0-127">[レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a6fc0-127">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 <span data-ttu-id="a6fc0-128">[レポート変数コレクションとグループ変数コレクションは &#40;レポートビルダーと SSRS&#41;を参照します。](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="a6fc0-128">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 [<span data-ttu-id="a6fc0-129">式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a6fc0-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
