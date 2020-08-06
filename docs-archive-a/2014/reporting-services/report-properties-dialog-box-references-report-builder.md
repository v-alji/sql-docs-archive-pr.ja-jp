---
title: '[参照] ([レポートのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c28e9053a1c13f8d0e0b7b44f3b1a037976c318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717391"
---
# <a name="report-properties-dialog-box-references-report-builder"></a><span data-ttu-id="9366b-102">[参照] ([レポートのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="9366b-102">Report Properties Dialog Box, References (Report Builder)</span></span>
  <span data-ttu-id="9366b-103">**[レポートのプロパティ]** ダイアログ ボックスの **[参照]** を選択すると、レポート定義内の式で使用される、カスタム アセンブリまたは他の外部アセンブリ、およびカスタム クラスのインスタンスへの参照を追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="9366b-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span> <span data-ttu-id="9366b-104">レポート ビルダーのローカル モードでは、カスタム アセンブリはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9366b-104">Custom assemblies are not supported in local mode in Report Builder.</span></span> <span data-ttu-id="9366b-105">カスタムアセンブリを使用するレポートを作成するには、でレポートデザイナーを使用し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9366b-105">To author reports that use custom assemblies, use Report Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="9366b-106">Options</span><span class="sxs-lookup"><span data-stu-id="9366b-106">Options</span></span>  
 <span data-ttu-id="9366b-107">**[アセンブリの追加または削除]**</span><span class="sxs-lookup"><span data-stu-id="9366b-107">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="9366b-108">レポートで参照されるアセンブリを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9366b-108">Lists the assemblies that the report references.</span></span> <span data-ttu-id="9366b-109">アセンブリは、レポートのデザインに使用するツールがインストールされているコンピューターおよびレポート サーバー上で使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9366b-109">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="9366b-110">参照の名前は、 **\<CodeModule>** レポート定義言語 (.rdl) ファイルのタグの内容と正確に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9366b-110">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="9366b-111">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="9366b-111">**Add**</span></span>  
 <span data-ttu-id="9366b-112">アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9366b-112">Click to add an assembly.</span></span> <span data-ttu-id="9366b-113">省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なアセンブリを選択します。</span><span class="sxs-lookup"><span data-stu-id="9366b-113">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="9366b-114">**削除**</span><span class="sxs-lookup"><span data-stu-id="9366b-114">**Remove**</span></span>  
 <span data-ttu-id="9366b-115">アセンブリの参照を一覧から削除するには、削除するアセンブリ名を選択し、 **[削除]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9366b-115">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="9366b-116">**[クラスの追加または削除]**</span><span class="sxs-lookup"><span data-stu-id="9366b-116">**Add or remove classes**</span></span>  
 <span data-ttu-id="9366b-117">レポートで使用されるクラスのインスタンスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9366b-117">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="9366b-118">クラスの一覧は、静的メンバーではなく、インスタンス ベースのメンバーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9366b-118">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="9366b-119">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="9366b-119">**Add**</span></span>  
 <span data-ttu-id="9366b-120">クラスの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9366b-120">Click to add a class reference.</span></span> <span data-ttu-id="9366b-121">省略記号ボタン ([...]) をクリックして [**開く**] ダイアログボックスを開き、レポートの処理および式の評価を完了するために必要なクラスを選択します。</span><span class="sxs-lookup"><span data-stu-id="9366b-121">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="9366b-122">**削除**</span><span class="sxs-lookup"><span data-stu-id="9366b-122">**Remove**</span></span>  
 <span data-ttu-id="9366b-123">クラスのインスタンスを削除するには、削除するインスタンスを選択し、 **[削除]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9366b-123">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="9366b-124">**設定**</span><span class="sxs-lookup"><span data-stu-id="9366b-124">**Up**</span></span>  
 <span data-ttu-id="9366b-125">依存関係のあるクラスについては、この参照の表示位置を一覧の上方に移動できます。</span><span class="sxs-lookup"><span data-stu-id="9366b-125">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="9366b-126">**[下へ]**</span><span class="sxs-lookup"><span data-stu-id="9366b-126">**Down**</span></span>  
 <span data-ttu-id="9366b-127">依存関係のあるクラスについては、この参照の表示位置を一覧の下方に移動できます。</span><span class="sxs-lookup"><span data-stu-id="9366b-127">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9366b-128">参照</span><span class="sxs-lookup"><span data-stu-id="9366b-128">See Also</span></span>  
 <span data-ttu-id="9366b-129">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="9366b-129">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="9366b-130">式 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9366b-130">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
