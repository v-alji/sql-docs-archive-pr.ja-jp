---
title: Azure HDInsight Pig Task | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afppigtask.f1
- sql11.dts.designer.afppigtask.f1
ms.assetid: 26f34f64-f344-486e-9190-acf71aef29a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 214db5e83272b1fa70c9e70eef8f8b9a43bac095
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633956"
---
# <a name="azure-hdinsight-pig-task"></a><span data-ttu-id="10f41-102">Azure HDInsight Pig Task</span><span class="sxs-lookup"><span data-stu-id="10f41-102">Azure HDInsight Pig Task</span></span>
<span data-ttu-id="10f41-103">Azure HDInsight クラスターで Pig スクリプトを実行するには、 **Azure HDInsight Pig Task** を使用します。</span><span class="sxs-lookup"><span data-stu-id="10f41-103">Use the **Azure HDInsight Pig Task** to run Pig script on an Azure HDInsight cluster.</span></span>
     
<span data-ttu-id="10f41-104">**Azure HDInsight Pig Task**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックします。すると、次の **[Azure HDInsight Pig Task Editor]** (Azure HDInsight Pig Task エディター) ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="10f41-104">To add an **Azure HDInsight Pig Task**, drag-drop it to the SSIS Designer, and double-click or right-click and click **Edit** to see the following **Azure HDInsight Pig Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="10f41-105">次の一覧で、このダイアログ ボックスのフィールドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="10f41-105">The following list describes fields in this dialog box.</span></span>  
  
1.  <span data-ttu-id="10f41-106">**[HDInsightConnection]** フィールドで、既存の Azure HDInsight 接続マネージャーを選択するか、スクリプトを実行するために使用される Azure HDInsight クラスターを参照する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="10f41-106">For the **HDInsightConnection** field, select an existing Azure HDInsight Connection Manager or create a new one that refers to the Azure HDInsight cluster used to execute the script.</span></span>
  
2.  <span data-ttu-id="10f41-107">**[AzureStorageConnection]** フィールドで、既存の Azure ストレージ接続マネージャーを選択するか、クラスターに関連付けられている Azure ストレージ アカウントを参照する新しいものを作成します。</span><span class="sxs-lookup"><span data-stu-id="10f41-107">For the **AzureStorageConnection** field, select an existing Azure Storage Connection Manager or create a new one that refers to the Azure Storage Account associated with the cluster.</span></span> <span data-ttu-id="10f41-108">これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="10f41-108">This is only necessary if you want to download the script execution output and error logs.</span></span>
 
3.  <span data-ttu-id="10f41-109">**[BlobContainer]** フィールドでは、クラスターに関連付けられているストレージ コンテナー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="10f41-109">For the **BlobContainer** field, specify the storage container name associated with the cluster.</span></span> <span data-ttu-id="10f41-110">これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="10f41-110">This is only necessary if you want to download the script execution output and error logs.</span></span>
  
4.  <span data-ttu-id="10f41-111">**[LocalLogFolder]** フィールドでは、スクリプト実行の出力およびエラー ログのダウンロード先となるフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="10f41-111">For the **LocalLogFolder** field, specify the folder to which the script execution output and error logs will be downloaded to.</span></span> <span data-ttu-id="10f41-112">これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="10f41-112">This is only necessary if you want to download the script execution output and error logs.</span></span>   
  
5.  <span data-ttu-id="10f41-113">実行する Pig スクリプトを指定するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="10f41-113">There are two ways to specify the Pig script to execute:</span></span>
  
    1.  <span data-ttu-id="10f41-114">**インライン スクリプト**: **[スクリプトの入力]** ダイアログ ボックスに実行するスクリプトをインラインで入力して、**[Script]** フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="10f41-114">**In-line script**: Specify the **Script** field by typing in-line the script to execute in the **Enter Script** dialog box.</span></span>
  
    2.  <span data-ttu-id="10f41-115">**スクリプト ファイル**: Azure Blob Storage にスクリプト ファイルをアップロードして、**[BlobName]** フィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="10f41-115">**Script file**: Upload the script file to Azure Blob Storage and specify the **BlobName** field.</span></span> <span data-ttu-id="10f41-116">BLOB が HDInsight クラスターに関連付けられている既定のストレージ アカウントまたはコンテナーにない場合は、**[ExternalStorageAccountName]** と **[ExternalBlobContainer]** フィールドを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10f41-116">If the blob is not in the default storage account or container associated with the HDInsight cluster, the **ExternalStorageAccountName** and **ExternalBlobContainer** fields must be specified.</span></span> <span data-ttu-id="10f41-117">外部 BLOB の場合は、パブリックにアクセス可能として構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="10f41-117">For an external blob, make sure that it is configured as publicly accessible.</span></span>  
  
     <span data-ttu-id="10f41-118">両方が指定されている場合、スクリプト ファイルが使用され、インライン スクリプトは無視されます。</span><span class="sxs-lookup"><span data-stu-id="10f41-118">If both are specified, script file will be used and the in-line script will be ignored.</span></span>
