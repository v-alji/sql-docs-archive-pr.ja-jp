---
title: データ品質プロジェクトの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.newdqproject.f1
helpviewer_keywords:
- create,data quality project
- data quality project,create
ms.assetid: 19c52d2b-d28e-4449-ab59-5fe0dc326cd9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bab14b34123464450bcf0de7540364fc642343e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712386"
---
# <a name="create-a-data-quality-project"></a><span data-ttu-id="5efb1-102">データ品質プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5efb1-102">Create a Data Quality Project</span></span>
  <span data-ttu-id="5efb1-103">このトピックでは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]を使用してデータ品質プロジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-103">This topic describes how to create a data quality project by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="5efb1-104">データ品質プロジェクトは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でクレンジングおよび照合アクティビティの実行に使用されます。</span><span class="sxs-lookup"><span data-stu-id="5efb1-104">A data quality project is used to run the cleansing or matching activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5efb1-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="5efb1-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="5efb1-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="5efb1-106">Prerequisites</span></span>  
 <span data-ttu-id="5efb1-107">データ品質プロジェジェクトでクレンジングおよび照合アクティビティに使用する関連のナレッジ ベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="5efb1-107">You must have a relevant knowledge base to use in the data quality project for the cleansing or matching activity.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5efb1-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5efb1-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5efb1-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="5efb1-109">Permissions</span></span>  
 <span data-ttu-id="5efb1-110">データ品質プロジェクトを作成するには、DQS_MAIN データベースに対する dqs_kb_editor または dqs_kb_operator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="5efb1-110">You must have the dqs_kb_editor or dqs_kb_operator role on the DQS_MAIN database to create a data quality project.</span></span>  
  
##  <a name="create-a-data-quality-project"></a><a name="Create"></a><span data-ttu-id="5efb1-111">データ品質プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="5efb1-111">Create a Data Quality Project</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="5efb1-112">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="5efb1-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] ホーム画面で、 **[新しいデータ品質プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5efb1-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New data quality project**.</span></span>  
  
3.  <span data-ttu-id="5efb1-114">**[新しいデータ品質プロジェクト]** 画面で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-114">In the **New Data Quality Project** screen:</span></span>  
  
    1.  <span data-ttu-id="5efb1-115">**[名前]** ボックスに新しいデータ品質プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-115">In the **Name** box, type a name for the new data quality project.</span></span>  
  
    2.  <span data-ttu-id="5efb1-116">(省略可能) **[説明]** ボックスに新しいデータ品質プロジェクトの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-116">(Optional) In the **Description** box, type a description for the new data quality project.</span></span>  
  
    3.  <span data-ttu-id="5efb1-117">**[ナレッジ ベースを使用する]** ボックスの一覧で、データ品質プロジェクトに使用するナレッジ ベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-117">In the **Use Knowledge base** list, click to select a knowledge base to be used for the data quality project.</span></span> <span data-ttu-id="5efb1-118">右側にある **[ナレッジ ベースの詳細: <ナレッジ ベース名>]** 領域に、選択したナレッジ ベースで使用可能なドメイン名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5efb1-118">The **Knowledge base details: <Knowledge_Base_Name>** area on the right side displays the domain names available in the selected knowledge base.</span></span>  
  
    4.  <span data-ttu-id="5efb1-119">**[アクティビティの選択]** 領域で、このデータ品質プロジェクトを使用して実行するアクティビティをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5efb1-119">In the **Select Activity** area, click on an activity that you want to perform using this data quality project:</span></span>  
  
        -   <span data-ttu-id="5efb1-120">**[クレンジング]**: ソース データをクレンジングするには、このアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-120">**Cleansing**: Select this activity to cleanse the source data.</span></span>  
  
        -   <span data-ttu-id="5efb1-121">**[照合]**: 照合を実行するには、このアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-121">**Matching**: Select this activity to perform matching.</span></span> <span data-ttu-id="5efb1-122">このアクティビティは、データ品質プロジェクトで選択されたナレッジ ベースに照合ポリシーが含まれている場合にのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="5efb1-122">This activity is available only if the knowledge base selected for the data quality project contains a matching policy.</span></span>  
  
4.  <span data-ttu-id="5efb1-123">**[作成]** をクリックし、データ品質プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5efb1-123">Click **Create** to create a data quality project.</span></span>  
  
##  <a name="follow-up-after-creating-a-data-quality-project"></a><a name="FollowUp"></a> <span data-ttu-id="5efb1-124">補足情報: データ品質プロジェクトを作成した後</span><span class="sxs-lookup"><span data-stu-id="5efb1-124">Follow Up: After Creating a Data Quality Project</span></span>  
 <span data-ttu-id="5efb1-125">データ品質プロジェクトを作成した後に、選択したアクティビティ (クレンジングと照合) の実行に使用するウィザードが示されます。</span><span class="sxs-lookup"><span data-stu-id="5efb1-125">After you create a data quality project, you are presented with a wizard that you use to perform the selected activity: cleansing or matching.</span></span> <span data-ttu-id="5efb1-126">クレンジングと照合アクティビティについて詳しくは、「[データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」および「[データ照合](../../2014/data-quality-services/data-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5efb1-126">For more information about the cleansing and matching activities, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md) and [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
