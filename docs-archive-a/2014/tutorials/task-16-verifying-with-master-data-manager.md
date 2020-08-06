---
title: 'タスク 16: マスターデータマネージャーによる検証 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715894"
---
# <a name="task-16-verifying-with-master-data-manager"></a><span data-ttu-id="4b674-102">タスク 16: マスター データ マネージャーを確認する</span><span class="sxs-lookup"><span data-stu-id="4b674-102">Task 16: Verifying with Master Data Manager</span></span>
  <span data-ttu-id="4b674-103">ここでは、マスター データ マネージャーを使用して、SSIS パッケージによって送信されたバッチ ジョブの状態をチェックし、データが MDS サーバーにアップロードされたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4b674-103">In this task, you check the status of the batch job submitted by the SSIS package and verify that the data was uploaded to MDS server by using Master Data Manager.</span></span>  
  
1.  <span data-ttu-id="4b674-104">**マスターデータマネージャー** ( `http://localhost/MDS` ) を起動します。</span><span class="sxs-lookup"><span data-stu-id="4b674-104">Launch **Master Data Manager** (`http://localhost/MDS`).</span></span> <span data-ttu-id="4b674-105">既に開いている場合は、上部にある [ **Microsoft SQL Server マスターデータサービス**をクリックして、**ホームページ**に移動します。</span><span class="sxs-lookup"><span data-stu-id="4b674-105">If it is already open, click **Microsoft SQL Server Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="4b674-106">[**統合管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b674-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="4b674-107">リストに送信した**Eimbatch**という名前のバッチがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b674-107">Notice that there is a batch with named **EIMBatch** that you submitted in the list.</span></span> <span data-ttu-id="4b674-108">次の画面が表示されない場合は、メニューバーの [**データのインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b674-108">Click **Import Data** on the menu bar if you do not see the following screen.</span></span>  
  
     <span data-ttu-id="4b674-109">![EIM バッチ](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM バッチ")</span><span class="sxs-lookup"><span data-stu-id="4b674-109">![EIM Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM Batch")</span></span>  
  
4.  <span data-ttu-id="4b674-110">上部にある [ **SQL Server 2012 マスターデータサービス**をクリックして、ホームページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b674-110">Switch back to the home page by click **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
5.  <span data-ttu-id="4b674-111">[**モデル**] に [**仕入先**モデル] が選択されていることを確認し、[**バージョン**] で [ **VERSION_1** ] が選択されていることを確認し、[**エクスプローラー**</span><span class="sxs-lookup"><span data-stu-id="4b674-111">Make sure that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**, and click **Explorer**.</span></span>  
  
6.  <span data-ttu-id="4b674-112">MDS にインポートされたデータの SSIS パッケージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4b674-112">You can see the data SSIS package imported into MDS.</span></span> <span data-ttu-id="4b674-113">データはクレンジングされ、重複する**コード**値はありません (注: Excel の [**仕入**先] 列は、MDS の Supplier エンティティの**code**属性に対応しています)。</span><span class="sxs-lookup"><span data-stu-id="4b674-113">The data should be cleansed and have no duplicates **Code** values (Note: **SupplierID** column in Excel corresponds to **Code** attribute of Supplier entity in MDS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="4b674-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="4b674-114">Next Step</span></span>  
 [<span data-ttu-id="4b674-115">タスク 17: SSIS パッケージによって作成された DQS クレンジング プロジェクトを確認する</span><span class="sxs-lookup"><span data-stu-id="4b674-115">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
