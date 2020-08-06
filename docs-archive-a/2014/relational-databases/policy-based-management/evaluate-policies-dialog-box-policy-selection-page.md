---
title: '[ポリシーの評価] ダイアログ ボックスの [ポリシーの選択] ページ | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f68a1ccc7873b6a05d2641ddaa87e8d5b0e5c6d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713038"
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a><span data-ttu-id="f7523-102">[ポリシーの評価] ダイアログ ボックスの [ポリシーの選択] ページ</span><span class="sxs-lookup"><span data-stu-id="f7523-102">Evaluate Policies Dialog Box, Policy Selection Page</span></span>
  <span data-ttu-id="f7523-103">このダイアログ ボックスを使用すると、ポリシー ベースの管理ポリシーを評価できます。</span><span class="sxs-lookup"><span data-stu-id="f7523-103">Use this dialog box to evaluate Policy-Based Management policies.</span></span> <span data-ttu-id="f7523-104">**[評価の結果]** ページを選択すると、ポリシーに準拠していない対象セット内の項目にポリシーを適用できます。</span><span class="sxs-lookup"><span data-stu-id="f7523-104">By selecting the **Evaluation Results** page, you can apply policies to the items in a target set that do not comply with the policies.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f7523-105">Options</span><span class="sxs-lookup"><span data-stu-id="f7523-105">Options</span></span>  
 <span data-ttu-id="f7523-106">**ソース**</span><span class="sxs-lookup"><span data-stu-id="f7523-106">**Source**</span></span>  
 <span data-ttu-id="f7523-107">ポリシーのソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7523-107">Specifies the source of the policies.</span></span> <span data-ttu-id="f7523-108">ソースを変更するには、参照ボタン (**[...]**) をクリックして、 **[ソースの選択]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="f7523-108">To change the source, click the Browse (**...**) button to open the **Select Source** dialog box.</span></span>  
  
 <span data-ttu-id="f7523-109">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="f7523-109">**Files**</span></span>  
 <span data-ttu-id="f7523-110">ポリシー ベースの管理ポリシーを含むファイルのパスを入力するか、参照ボタン (**[...]**) を使用してファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f7523-110">Type the path of a file that contains a Policy-Based Management policy, or use the Browse (**...**) button to select the file.</span></span>  
  
 <span data-ttu-id="f7523-111">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="f7523-111">**Server**</span></span>  
 <span data-ttu-id="f7523-112">必要なポリシーを含む [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="f7523-112">Select to connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that contains the policy that you want.</span></span>  
  
 <span data-ttu-id="f7523-113">**[ポリシー: ポリシー]**</span><span class="sxs-lookup"><span data-stu-id="f7523-113">**Policies: Policy**</span></span>  
 <span data-ttu-id="f7523-114">クリックすると、指定したポリシーの [ポリシー] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="f7523-114">Click to open the policy dialog box for the specified policy.</span></span>  
  
 <span data-ttu-id="f7523-115">**[ポリシー: カテゴリ]**</span><span class="sxs-lookup"><span data-stu-id="f7523-115">**Policies: Category**</span></span>  
 <span data-ttu-id="f7523-116">ポリシーのカテゴリ。</span><span class="sxs-lookup"><span data-stu-id="f7523-116">The category of the policy.</span></span> <span data-ttu-id="f7523-117">このボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="f7523-117">This box is read-only.</span></span>  
  
 <span data-ttu-id="f7523-118">**[ポリシー: ファセット]**</span><span class="sxs-lookup"><span data-stu-id="f7523-118">**Policies: Facet**</span></span>  
 <span data-ttu-id="f7523-119">ポリシーによって実装されるファセット。</span><span class="sxs-lookup"><span data-stu-id="f7523-119">The facet implemented by the policy.</span></span> <span data-ttu-id="f7523-120">このボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="f7523-120">This box is read-only.</span></span>  
  
 <span data-ttu-id="f7523-121">**Evaluate**</span><span class="sxs-lookup"><span data-stu-id="f7523-121">**Evaluate**</span></span>  
 <span data-ttu-id="f7523-122">ポリシーを評価モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="f7523-122">Runs the policy in evaluation mode.</span></span> <span data-ttu-id="f7523-123">これにより対象セットの準拠レポートが生成されますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再構成されたり、今後の準拠が適用されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="f7523-123">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span>  
  
## <a name="possible-errors"></a><span data-ttu-id="f7523-124">発生する可能性のあるエラー</span><span class="sxs-lookup"><span data-stu-id="f7523-124">Possible Errors</span></span>  
  
-   <span data-ttu-id="f7523-125">**対象が見つかりません**</span><span class="sxs-lookup"><span data-stu-id="f7523-125">**No targets found**</span></span>  
  
     <span data-ttu-id="f7523-126">対象セットは、次のいずれかの理由により空になっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f7523-126">The target set could be empty due to any of the following reasons:</span></span>  
  
    -   <span data-ttu-id="f7523-127">ポリシーで指定された型の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対象が存在しない。</span><span class="sxs-lookup"><span data-stu-id="f7523-127">There are no targets on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of the type specified by the policy.</span></span>  
  
    -   <span data-ttu-id="f7523-128">サーバーの制限によって対象を含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが除外されている。</span><span class="sxs-lookup"><span data-stu-id="f7523-128">The server restriction might exclude the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains the target.</span></span>  
  
    -   <span data-ttu-id="f7523-129">ポリシーがデータベース内のオブジェクト (テーブル、ビュー、ユーザーなど) を対象としている場合に、データベースがポリシーのカテゴリをサブスクライブしていない。</span><span class="sxs-lookup"><span data-stu-id="f7523-129">If the policy is on an object in a database (for example a table, view, or user) the database might not subscribe to the category of the policy.</span></span>  
  
    -   <span data-ttu-id="f7523-130">対象セットのフィルターによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのインスタンスのすべての対象が除外されている。</span><span class="sxs-lookup"><span data-stu-id="f7523-130">The target-set filter might exclude all targets on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="f7523-131">ターゲット サーバーの種類とポリシーが評価されるサーバーの種類が異なっている。</span><span class="sxs-lookup"><span data-stu-id="f7523-131">The target server type is different from the server type on which the policy is evaluated.</span></span> <span data-ttu-id="f7523-132">たとえば、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]用に作成されたポリシーを評価しようとすると、空の対象セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="f7523-132">For example, in the [!INCLUDE[ssDE](../../includes/ssde-md.md)], if you try to evaluate a policy that has been created for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you will receive an empty target set</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7523-133">参照</span><span class="sxs-lookup"><span data-stu-id="f7523-133">See Also</span></span>  
 <span data-ttu-id="f7523-134">[ポリシーベースの管理を使用してサーバーを管理する](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="f7523-134">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 <span data-ttu-id="f7523-135">[[ポリシーの評価] ダイアログ ボックスの [評価の結果] ページ](evaluate-policies-dialog-box-evaluation-results-page.md)</span><span class="sxs-lookup"><span data-stu-id="f7523-135">[Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)</span></span>  
  
  
