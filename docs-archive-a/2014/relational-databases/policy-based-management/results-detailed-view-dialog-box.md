---
title: '[結果の詳細ビュー] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.results.f1
- sql12.swb.dmf.policy.resultdetails.f1
ms.assetid: 366f0ff8-722a-40a9-934f-854147e4933d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c4d669fb1546d27eb8b6ae78e0de8dea5975f24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740862"
---
# <a name="results-detailed-view-dialog-box"></a><span data-ttu-id="5ad18-102">[結果の詳細ビュー] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="5ad18-102">Results Detailed View Dialog Box</span></span>
  <span data-ttu-id="5ad18-103">**[ポリシーの評価]** ダイアログ ボックスを使用してポリシーを実行し、 **[評価]** をクリックすると、このダイアログ ボックスにポリシーの評価結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5ad18-103">This dialog box shows the results of policy evaluation after you have run a policy by using the **Evaluate Policies** dialog box and clicked **Evaluate**.</span></span> <span data-ttu-id="5ad18-104">このダイアログ ボックスは読み取り専用で、プロパティ式のどの部分に問題があるかを把握するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5ad18-104">This dialog box is read-only, and helps you understand which part of a property expression might be failing.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5ad18-105">オプション</span><span class="sxs-lookup"><span data-stu-id="5ad18-105">Options</span></span>  
 <span data-ttu-id="5ad18-106">**[AndOr]**</span><span class="sxs-lookup"><span data-stu-id="5ad18-106">**AndOr**</span></span>  
 <span data-ttu-id="5ad18-107">複数のプロパティ式がある場合に、プロパティ式を累積するか、選択するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ad18-107">When more than one property expression is present, indicates whether the property expressions are cumulative or alternative.</span></span>  
  
 <span data-ttu-id="5ad18-108">**結果**</span><span class="sxs-lookup"><span data-stu-id="5ad18-108">**Result**</span></span>  
 <span data-ttu-id="5ad18-109">プロパティ式の成功または失敗を表すアイコン。</span><span class="sxs-lookup"><span data-stu-id="5ad18-109">Icon that represents the success or failure of the property expression.</span></span>  
  
 <span data-ttu-id="5ad18-110">**フィールド**</span><span class="sxs-lookup"><span data-stu-id="5ad18-110">**Field**</span></span>  
 <span data-ttu-id="5ad18-111">モデル化されるファセットのプロパティ。</span><span class="sxs-lookup"><span data-stu-id="5ad18-111">The property of the facet that is being modeled.</span></span>  
  
 <span data-ttu-id="5ad18-112">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="5ad18-112">**Operator**</span></span>  
 <span data-ttu-id="5ad18-113">式の演算子。 **=** 、 **Like**などがあります。</span><span class="sxs-lookup"><span data-stu-id="5ad18-113">The operator for the expression, for example **=** or **Like**.</span></span>  
  
 <span data-ttu-id="5ad18-114">**予期された値**</span><span class="sxs-lookup"><span data-stu-id="5ad18-114">**Expected Value**</span></span>  
 <span data-ttu-id="5ad18-115">プロパティ式が成功するために必要なフィールドの値。</span><span class="sxs-lookup"><span data-stu-id="5ad18-115">The value for the field that will cause the property expression to be successful.</span></span>  
  
 <span data-ttu-id="5ad18-116">**[実際の値]**</span><span class="sxs-lookup"><span data-stu-id="5ad18-116">**Actual Value**</span></span>  
 <span data-ttu-id="5ad18-117">ポリシーによって検出されたフィールドの値。</span><span class="sxs-lookup"><span data-stu-id="5ad18-117">The value for the field that was detected by the policy.</span></span>  
  
 <span data-ttu-id="5ad18-118">**[ポリシーの説明]**</span><span class="sxs-lookup"><span data-stu-id="5ad18-118">**Policy description**</span></span>  
 <span data-ttu-id="5ad18-119">ポリシーの説明。</span><span class="sxs-lookup"><span data-stu-id="5ad18-119">The description of the policy.</span></span>  
  
 <span data-ttu-id="5ad18-120">**追加のヘルプ**</span><span class="sxs-lookup"><span data-stu-id="5ad18-120">**Additional help**</span></span>  
 <span data-ttu-id="5ad18-121">ハイパーリンクをクリックすると、このポリシーに関連する Web ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="5ad18-121">Click the hyperlink to open a Web page that is related to this policy.</span></span> <span data-ttu-id="5ad18-122">追加のヘルプ ハイパーリンクは、ポリシーの作成時に構成され、空白である場合や使用できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ad18-122">The Additional Help hyperlink is configured when the policy is created and might be blank or unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad18-123">参照</span><span class="sxs-lookup"><span data-stu-id="5ad18-123">See Also</span></span>  
 <span data-ttu-id="5ad18-124">[[ポリシー管理] ノード &#40;オブジェクト エクスプローラー&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="5ad18-124">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="5ad18-125">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="5ad18-125">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
