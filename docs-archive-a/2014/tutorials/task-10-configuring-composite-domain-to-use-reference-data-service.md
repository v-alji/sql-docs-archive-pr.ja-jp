---
title: 'タスク 10: 参照データサービスを使用するように複合ドメインを構成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d70966b4cde110540bf5008eda4e3151fe32f28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742706"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a><span data-ttu-id="afaa5-102">タスク 10: 参照データ サービスを使用して複合ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="afaa5-102">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>
  <span data-ttu-id="afaa5-103">このタスクでは、 **Melissa Check**サービスを使用するように**Address Validation**複合ドメインを構成します。</span><span class="sxs-lookup"><span data-stu-id="afaa5-103">In this task, you configure the **Address Validation** composite domain to use the **Melissa Data - Address Check** service.</span></span> <span data-ttu-id="afaa5-104">実行時のクレンジング アクティビティでは、クレンジングのために Address Validation ドメインのドメイン値が DQS からこのサービスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="afaa5-104">At runtime, during cleansing activity, DQS passes the values of domains in the Address Validation domain to the service for cleansing.</span></span> <span data-ttu-id="afaa5-105">詳細については、「[参照データへのドメインまたは複合ドメインのマップ」を](https://msdn.microsoft.com/library/hh213030.aspx)参照してください。</span><span class="sxs-lookup"><span data-stu-id="afaa5-105">See [Map Domain/Composite Domain to Reference Data](https://msdn.microsoft.com/library/hh213030.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="afaa5-106">**DQS クライアント**のメインページで、[**最近使用したナレッジベース**] の下の [**サプライヤー (ドメイン管理)** ] をクリックして、[**ドメイン管理**] ページを起動します。</span><span class="sxs-lookup"><span data-stu-id="afaa5-106">In the main page of **DQS Client**, click **Suppliers (Domain Management)** under **Recent Knowledge Bases** to launch the **Domain Management** page.</span></span>  
  
2.  <span data-ttu-id="afaa5-107">**ドメインの一覧**で [**アドレス検証**複合ドメイン] を選択します。</span><span class="sxs-lookup"><span data-stu-id="afaa5-107">Select the **Address Validation** composite domain in the **list of domains**.</span></span>  
  
3.  <span data-ttu-id="afaa5-108">右ペインで、[**参照データ**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="afaa5-108">In the right pane, switch to the **Reference Data** tab.</span></span>  
  
     <span data-ttu-id="afaa5-109">![[参照データ] タブ](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "[参照データ] タブ")</span><span class="sxs-lookup"><span data-stu-id="afaa5-109">![Reference Data Tab](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Reference Data Tab")</span></span>  
  
4.  <span data-ttu-id="afaa5-110">ツールバーの [**参照**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="afaa5-110">Click **Browse** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="afaa5-111">[**オンライン参照データプロバイダーのカタログ**] ダイアログボックスで、 **Melissa**の横の**チェックボックス**をオンにします。</span><span class="sxs-lookup"><span data-stu-id="afaa5-111">On the **Online Reference Data Providers Catalog** dialog box, select **check box** next to **Melissa Data - Address Check**.</span></span>  
  
     <span data-ttu-id="afaa5-112">![[メリッサ データ - アドレスをチェック] の選択](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "[メリッサ データ - アドレスをチェック] の選択")</span><span class="sxs-lookup"><span data-stu-id="afaa5-112">![Select Melissa Data - Address Check](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Select Melissa Data - Address Check")</span></span>  
  
6.  <span data-ttu-id="afaa5-113">右側のウィンドウの [**スキーマ**] セクションで、ドロップダウンリストを使用して**アドレス行**ドメインを**アドレス行 (M)** スキーマ項目にマップします。</span><span class="sxs-lookup"><span data-stu-id="afaa5-113">In the right pane, in the **Schema** section, map **Address Line** domain to the **Address Line (M)** schema item by using the drop-down list.</span></span>  
  
     <span data-ttu-id="afaa5-114">![RDS スキーマのアイテムをドメインにマップ](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "RDS スキーマのアイテムをドメインにマップ")</span><span class="sxs-lookup"><span data-stu-id="afaa5-114">![Map RDS Schema Item to Domain](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Map RDS Schema Item to Domain")</span></span>  
  
7.  <span data-ttu-id="afaa5-115">ツールバーの [**スキーマエントリの追加] (+)** ボタンをクリックして、一覧にエントリを作成します。</span><span class="sxs-lookup"><span data-stu-id="afaa5-115">Click **Add Schema Entry (+)** button on the toolbar to create an entry in the list.</span></span>  
  
     <span data-ttu-id="afaa5-116">![[スキーマ エントリの追加] ツール バー ボタン](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "[スキーマ エントリの追加] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="afaa5-116">![Add Schema Entry Toolbar Button](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Add Schema Entry Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="afaa5-117">次の図に示すように、ドロップダウン リストを使用して次の DQS ドメインをマップします。</span><span class="sxs-lookup"><span data-stu-id="afaa5-117">Map the following DQS domains by using the drop-down lists as shown in the following picture.</span></span>  
  
     <span data-ttu-id="afaa5-118">![RDS スキーマ項目をドメインにマップする](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "RDS スキーマ項目をドメインにマップする")</span><span class="sxs-lookup"><span data-stu-id="afaa5-118">![Map RDS Schema Items to Domains](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Map RDS Schema Items to Domains")</span></span>  
  
9. <span data-ttu-id="afaa5-119">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="afaa5-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="afaa5-120">次の手順</span><span class="sxs-lookup"><span data-stu-id="afaa5-120">Next Step</span></span>  
 [<span data-ttu-id="afaa5-121">タスク 11: ナレッジ ベースをパブリッシュする</span><span class="sxs-lookup"><span data-stu-id="afaa5-121">Task 11: Publishing the Knowledge Base</span></span>](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
