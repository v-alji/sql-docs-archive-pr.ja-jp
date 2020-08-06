---
title: MDS リポジトリへの接続 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c1db0594f07da7ff8a78642e4b2de0eb9e507164
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714474"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a><span data-ttu-id="30690-102">MDS リポジトリへの接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="30690-102">Connect to an MDS Repository (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="30690-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、データの読み込みまたはパブリッシュの前に MDS リポジトリに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30690-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must connect to an MDS repository before you can load or publish data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="30690-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="30690-104">Prerequisites</span></span>  
 <span data-ttu-id="30690-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="30690-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="30690-106">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="30690-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-connect-to-an-mds-repository"></a><span data-ttu-id="30690-107">MDS リポジトリに接続するには</span><span class="sxs-lookup"><span data-stu-id="30690-107">To connect to an MDS repository</span></span>  
  
1.  <span data-ttu-id="30690-108">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]の **[マスター データ]** タブの **[接続と読み込み]** グループで、 **[接続]** ボタンの下の矢印をクリックし、 **[接続の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30690-108">In the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], on the **Master Data** tab, in the **Connect and Load** group, click the arrow under the **Connect** button and click **Manage Connections**.</span></span>  
  
2.  <span data-ttu-id="30690-109">**[接続の管理]** ダイアログ ボックスの **[新しい接続]** セクションで、 **[新しい接続の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30690-109">On the **Manage Connections** dialog box, in the **New connection** section, click **Create a new connection**.</span></span>  
  
3.  <span data-ttu-id="30690-110">**[新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30690-110">Click **New**.</span></span>  
  
4.  <span data-ttu-id="30690-111">**[新しい接続の追加]** ダイアログ ボックスの **[説明]** フィールドに、接続の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="30690-111">On the **Add New Connection** dialog box, in the **Description** field, type a description for your connection.</span></span> <span data-ttu-id="30690-112">この接続は、ツール バーの **[接続]** ボタンの下の矢印をクリックしたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="30690-112">This connection will be displayed when you click the arrow under the **Connect** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="30690-113">**[MDS サーバー アドレス]** ボックスに、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL (http://contoso/mds など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="30690-113">In the **MDS server address** box, type the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30690-114">必ずコンピューター名を使用してください。"localhost" を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="30690-114">Ensure that you use the computer name; do not use "localhost".</span></span>  
  
6.  <span data-ttu-id="30690-115">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30690-115">Click **OK**.</span></span> <span data-ttu-id="30690-116">**[既存の接続]** セクションに名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="30690-116">The name is displayed in the **Existing Connections** section.</span></span>  
  
7.  <span data-ttu-id="30690-117">必要であれば、 **[テスト]** をクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="30690-117">Optionally, click **Test** to test the connection.</span></span> <span data-ttu-id="30690-118">確認ダイアログまたはエラー ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30690-118">A confirmation or error dialog is displayed.</span></span> <span data-ttu-id="30690-119">**[OK]** をクリックして閉じます。</span><span class="sxs-lookup"><span data-stu-id="30690-119">Click **OK** to close it.</span></span>  
  
8.  <span data-ttu-id="30690-120">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30690-120">Click **Connect**.</span></span> <span data-ttu-id="30690-121">**[マスター データ サービス]** ペインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30690-121">The **Master Data Services** pane is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="30690-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="30690-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="30690-123">MDS から Excel へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="30690-123">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)  
  
-   [<span data-ttu-id="30690-124">&#40;Excel 用 MDS アドインを読み込む前にデータをフィルター処理する&#41;</span><span class="sxs-lookup"><span data-stu-id="30690-124">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="30690-125">参照</span><span class="sxs-lookup"><span data-stu-id="30690-125">See Also</span></span>  
 [<span data-ttu-id="30690-126">接続 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="30690-126">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
  
