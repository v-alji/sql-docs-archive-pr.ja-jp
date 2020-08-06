---
title: DQS の既定のナレッジ ベースの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3261c7af28bb5710ede203d1fe27c6540286e9f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633303"
---
# <a name="using-the-dqs-default-knowledge-base"></a><span data-ttu-id="ff80e-102">DQS の既定のナレッジ ベースの使用</span><span class="sxs-lookup"><span data-stu-id="ff80e-102">Using the DQS Default Knowledge Base</span></span>
  <span data-ttu-id="ff80e-103">このトピックでは、 **(DQS) にインストールされている既定のナレッジ ベース、** DQS データ [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-103">This topic describes the default knowledge base, **DQS Data**, which is installed with [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="ff80e-104">これは、次のドメインを含む、あらかじめ構築された既定のナレッジ ベースです。</span><span class="sxs-lookup"><span data-stu-id="ff80e-104">This is a pre-built default knowledge base that contains the following domains:</span></span>  
  
-   <span data-ttu-id="ff80e-105">**国/地域**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、各地域の 3 桁のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-105">**Country/Region**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="ff80e-106">先頭の値は長い名前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-106">Leading value is set to the long country name.</span></span>  
  
-   <span data-ttu-id="ff80e-107">**国/地域 (3 文字が先頭)**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、および 3 桁のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-107">**Country/Region (three-letter leading)**: Contains the conventional long (official name as designated by the country/region) and short names (common name used in lists, on maps, and so on), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="ff80e-108">先頭の値は、3 文字の省略形に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-108">Leading values is set to County three-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="ff80e-109">**国/地域 (2 文字が先頭)**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、各地域の 3 桁のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-109">**Country/Region (two-letter leading)**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="ff80e-110">先頭の値は、2 文字の省略形に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-110">Leading value is set to the Country two-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="ff80e-111">**米国 - 郡**: 米国の郡の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ff80e-111">**US - Counties**: Contains a list of US counties.</span></span>  
  
-   <span data-ttu-id="ff80e-112">**米国 - 姓**: 2000 年の国勢調査で 100 例以上登録された姓の一覧です。</span><span class="sxs-lookup"><span data-stu-id="ff80e-112">**US - Last Name**: Contains a list of last names (surnames) occurring 100 or more times in the Census 2000.</span></span>  
  
-   <span data-ttu-id="ff80e-113">**米国 - 場所 -**: 2010 年の国勢調査から抽出された、50 州、コロンビア特別区、およびプエルトリコの地域の一覧です。</span><span class="sxs-lookup"><span data-stu-id="ff80e-113">**US - Places**: Contains a list of places for the 50 states, the District of Columbia, and Puerto Rico extracted from the Census 2010.</span></span>  
  
-   <span data-ttu-id="ff80e-114">**米国 - 州**: 米国の各州の通常の長い (公式) の名前と 2 文字の省略形が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-114">**US - State**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="ff80e-115">先頭の値は通常の州名に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-115">Leading value is set to the conventional state name.</span></span>  
  
-   <span data-ttu-id="ff80e-116">**米国 - 州 (2 文字の省略形)**: 米国の各州の通常の長い (公式) の名前と 2 文字の省略形が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-116">**US - State (2-letter heading)**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="ff80e-117">先頭の値は、州名の 2 文字の省略形に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff80e-117">Leading value is set to the two-letter abbreviation state name.</span></span>  
  
## <a name="using-the-default-knowledge-base"></a><span data-ttu-id="ff80e-118">既定のナレッジ ベースの使用</span><span class="sxs-lookup"><span data-stu-id="ff80e-118">Using the Default Knowledge Base</span></span>  
 <span data-ttu-id="ff80e-119">既定の DQS ナレッジ ベースである DQS データは、次の方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-119">You can use the default DQS knowledge base, DQS Data, in the following ways:</span></span>  
  
-   <span data-ttu-id="ff80e-120">既定のナレッジ ベースを使用してクレンジング データ品質プロジェクトを開始して実行します。先に DQS の新しいナレッジ ベースを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ff80e-120">Quickly start and run a cleansing data quality project using the default knowledge base without first having to create a new knowledge base in DQS.</span></span>  
  
-   <span data-ttu-id="ff80e-121">既定のナレッジ ベースで、ドメイン管理、ナレッジ検出、または照合ポリシーのアクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-121">Run the Domain Management, Knowledge Discovery, or Matching Policy activities on the default knowledge base.</span></span> <span data-ttu-id="ff80e-122">これを実行するには、 **Data Quality Client Home Screen** の [[ナレッジ ベースを開く]](../../2014/data-quality-services/data-quality-client-home-screen.md)をクリックし、 **[ナレッジ ベースを開く]** 画面の **[DQS Data]** ナレッジ ベースを選択して、 **[アクティビティの選択]** 領域で必要なアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-122">To do so, click **Open Knowledge Base** in the [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), select the **DQS Data** knowledge base in the **Open Knowledge Base** screen, and then select the required activity in the **Select Activity** area.</span></span> <span data-ttu-id="ff80e-123">**[次へ]** をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-123">Click **Next** to proceed.</span></span>  
  
-   <span data-ttu-id="ff80e-124">既定のナレッジ ベースを使用して新しいナレッジ ベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-124">Create a new knowledge base using the default knowledge base.</span></span> <span data-ttu-id="ff80e-125">既存のナレッジ ベースからナレッジ ベースを作成する方法については、「 [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff80e-125">To create a knowledge base from an existing knowledge base, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).</span></span>  
  
-   <span data-ttu-id="ff80e-126">「 [Integration Services の DQS クレンジング コンポーネント](https://go.microsoft.com/fwlink/?LinkId=238830) 」および「 [Excel 用マスター データ サービス アドイン](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)」で、それを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff80e-126">Use it in the [DQS Cleansing component in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) and [Master Data Services Add-in for Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff80e-127">参照</span><span class="sxs-lookup"><span data-stu-id="ff80e-127">See Also</span></span>  
 [<span data-ttu-id="ff80e-128">DQS のナレッジ ベースとドメイン</span><span class="sxs-lookup"><span data-stu-id="ff80e-128">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
