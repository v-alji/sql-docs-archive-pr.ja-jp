---
title: 'レッスン 2 : 接続情報の指定 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715106"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a><span data-ttu-id="b4cc2-102">レッスン 2 : 接続情報の指定 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b4cc2-102">Lesson 2: Specifying Connection Information (Reporting Services)</span></span>
  <span data-ttu-id="b4cc2-103">チュートリアル プロジェクトにレポートを追加した後、リレーショナル データベース、多次元データベース、その他のリソースのデータにアクセスするためにレポートで使用される接続情報である *データ ソース*を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-103">After you add a report to the Tutorial project, you need to define a *data source*, which is connection information the report uses to access data from either a relational database, multidimensional database, or other resource.</span></span>  
  
 <span data-ttu-id="b4cc2-104">このレッスンでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] サンプル データベースをデータ ソースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-104">In this lesson, you will use the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database as your data source.</span></span> <span data-ttu-id="b4cc2-105">このチュートリアルでは、このデータベースが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ローカルコンピューターにインストールされているの既定のインスタンスに配置されていることを前提としてい [!INCLUDE[ssDE](../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-105">This tutorial assumes that this database is located in a default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed on your local computer.</span></span>  
  
### <a name="to-set-up-a-connection"></a><span data-ttu-id="b4cc2-106">接続を設定するには</span><span class="sxs-lookup"><span data-stu-id="b4cc2-106">To set up a connection</span></span>  
  
1.  <span data-ttu-id="b4cc2-107">**レポートデータ**ペインで、[**新規作成**] をクリックし、[**データソース...**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-107">In the **Report Data** pane, click **New** and then click **Data Source...**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4cc2-108">**レポート データ** ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-108">If the **Report Data** pane is not visible, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="b4cc2-109">**[名前]** に「 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-109">In **Name**, type [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].</span></span>  
  
3.  <span data-ttu-id="b4cc2-110">**[埋め込み接続]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-110">Make sure **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="b4cc2-111">**[種類]** で **[Microsoft SQL Server]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-111">In **Type**, select **Microsoft SQL Server**.</span></span>  
  
5.  <span data-ttu-id="b4cc2-112">**[接続文字列]** に次を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-112">In **Connection string**, type the following:</span></span>  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     <span data-ttu-id="b4cc2-113">この接続文字列は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、レポート サーバー、および [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースがすべてローカル コンピューターにインストールされていることと、ユーザーが [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースにログオンする権限を持っていることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-113">This connection string assumes that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the report server, and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database are all installed on the local computer and that you have permission to log on to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b4cc2-114">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services または名前付きインスタンスを使用している場合は、接続文字列にインスタンス情報を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-114">If you are using [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services or a named instance, the connection string must include instance information:</span></span>  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  <span data-ttu-id="b4cc2-115">接続文字列の詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](data-connections-data-sources-and-connection-strings-in-reporting-services.md)」および「 [[データソースのプロパティ] ダイアログボックス-全般](data-source-properties-dialog-box-general.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-115">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) and [Data Source Properties Dialog Box, General](data-source-properties-dialog-box-general.md).</span></span>  
  
6.  <span data-ttu-id="b4cc2-116">左ペインで **[資格情報]** をクリックし、 **[Windows 認証 (統合セキュリティ) を使用する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-116">Click **Credentials** in the left pane and click **Use Windows Authentication (integrated security)**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="b4cc2-117">データソース [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] が**レポートデータ**ペインに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-117">data source [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] is added to the **Report Data** pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="b4cc2-118">次の作業</span><span class="sxs-lookup"><span data-stu-id="b4cc2-118">Next Task</span></span>  
 <span data-ttu-id="b4cc2-119">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] サンプル データベースへの接続が正常に定義されました。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-119">You have successfully defined a connection to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b4cc2-120">次に、レポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-120">Next, you will create the report.</span></span> <span data-ttu-id="b4cc2-121">「[レッスン 3: テーブル レポートのデータセットの定義 &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4cc2-121">See [Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cc2-122">参照</span><span class="sxs-lookup"><span data-stu-id="b4cc2-122">See Also</span></span>  
 [<span data-ttu-id="b4cc2-123">Reporting Services でのデータ接続、データ ソース、および接続文字列</span><span class="sxs-lookup"><span data-stu-id="b4cc2-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
