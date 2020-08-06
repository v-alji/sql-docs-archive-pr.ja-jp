---
title: ポリシーをスケジュールする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1bce1b9d650606e9485899c34c72ca6b27a72dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720450"
---
# <a name="schedule-the-policies"></a><span data-ttu-id="e3cad-102">ポリシーのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="e3cad-102">Schedule the Policies</span></span>
  <span data-ttu-id="e3cad-103">ここでは、前の作業でインポートしたベスト プラクティス ポリシーをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-103">In this task, you will schedule the best practices policies that you imported in the previous task.</span></span>  
  
### <a name="to-schedule-the-best-practices-policies"></a><span data-ttu-id="e3cad-104">ベスト プラクティス ポリシーをスケジュールするには</span><span class="sxs-lookup"><span data-stu-id="e3cad-104">To schedule the best practices policies</span></span>  
  
1.  <span data-ttu-id="e3cad-105">オブジェクトエクスプローラーで、[**管理**]、[**ポリシー管理**]、[**ポリシー**] の順に展開し、ベストプラクティスポリシーを右クリックして、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-105">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Policies**, right-click a best practices policy, and then click **Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3cad-106">または、ベストプラクティスに関連付けられているポリシーを簡単に確認し、ベストプラクティスのカテゴリを並べ替えるには、[**管理**]、[**ポリシー管理**] の順に展開し、[**ポリシー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-106">As an alternative, to easily see which policies are associated with best practices and to sort the best practices categories, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span> <span data-ttu-id="e3cad-107">**[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-107">On the **View** menu, click **Object Explorer Details**.</span></span> <span data-ttu-id="e3cad-108">オブジェクトエクスプローラーの**詳細**ペインで、[**カテゴリ**] 見出しをクリックして、ポリシーをカテゴリ別に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="e3cad-108">In the **Object Explorer Details** pane, click the **Category** heading to sort the policies by category.</span></span> <span data-ttu-id="e3cad-109">ベストプラクティスポリシーには、「 **Microsoft のベストプラクティス**」というプレフィックスが付いています。</span><span class="sxs-lookup"><span data-stu-id="e3cad-109">The best practices policies have the prefix **Microsoft Best Practices**.</span></span> <span data-ttu-id="e3cad-110">構成するポリシーを右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-110">Right-click the policy that you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e3cad-111">[**ポリシーを開く**] ダイアログボックスの **[全般**] ページで、[**評価モード**] ボックスの一覧の [**スケジュール設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-111">On the **General** page of the **Open Policy** dialog box, in the **Evaluation Mode** list, click **On schedule**.</span></span>  
  
3.  <span data-ttu-id="e3cad-112">[**スケジュール**] ボックスの横にある [**選択**] をクリックして既存のスケジュールを指定するか、[**新規**作成] をクリックして新しいスケジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="e3cad-112">Next to the **Schedule** box, click **Pick** to specify an existing schedule, or click **New** to create a new schedule.</span></span>  
  
4.  <span data-ttu-id="e3cad-113">スケジュールを構成した後は、ページの上部付近にある [**有効**] チェックボックスをオンにして、スケジュールされたポリシーを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e3cad-113">After you have configured a schedule, you can select the **Enabled** check box near the top of the page to enable the scheduled policy.</span></span>  
  
5.  <span data-ttu-id="e3cad-114">スケジュールするポリシーごとに、手順 1. ～ 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e3cad-114">Repeats steps 1 through 4 for each policy that you want to schedule.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e3cad-115">スケジュールされたポリシーが実行された後に評価結果を表示するには、対象インスタンスのポリシー履歴ログを開きます。</span><span class="sxs-lookup"><span data-stu-id="e3cad-115">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="e3cad-116">ログを開くには、[**ポリシー管理**] を右クリックし、[**履歴の表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e3cad-116">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e3cad-117">まとめ</span><span class="sxs-lookup"><span data-stu-id="e3cad-117">Summary</span></span>  
 <span data-ttu-id="e3cad-118">スケジュールしたポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一インスタンス上で実行するよう構成しました。</span><span class="sxs-lookup"><span data-stu-id="e3cad-118">You configured scheduled policies to run on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e3cad-119">スケジュールしたポリシーを複数のインスタンスに配置するには、このチュートリアルの次の作業に進みます。</span><span class="sxs-lookup"><span data-stu-id="e3cad-119">If you want to deploy scheduled policies to multiple instances, continue to the next task in this tutorial.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e3cad-120">次の手順</span><span class="sxs-lookup"><span data-stu-id="e3cad-120">Next Steps</span></span>  
 [<span data-ttu-id="e3cad-121">スケジュールされたポリシーの複数インスタンスへの配置</span><span class="sxs-lookup"><span data-stu-id="e3cad-121">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
