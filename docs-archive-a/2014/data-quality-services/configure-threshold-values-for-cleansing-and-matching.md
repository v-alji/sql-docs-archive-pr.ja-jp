---
title: クレンジングと照合のしきい値の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0faf64e96468a3a9aac0de12d3ec3acbb1e1ed85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712402"
---
# <a name="configure-threshold-values-for-cleansing-and-matching"></a><span data-ttu-id="59c41-102">クレンジングと照合のしきい値の構成</span><span class="sxs-lookup"><span data-stu-id="59c41-102">Configure Threshold Values for Cleansing and Matching</span></span>
  <span data-ttu-id="59c41-103">このトピックでは、コンピューター支援型のクレンジングおよび照合アクティビティの最中に [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で使用されるしきい値を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59c41-103">This topic describes how to configure threshold values that will be used during the computer-assisted cleansing and matching activities in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="59c41-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="59c41-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="59c41-105">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="59c41-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="59c41-106">Permissions</span><span class="sxs-lookup"><span data-stu-id="59c41-106">Permissions</span></span>  
 <span data-ttu-id="59c41-107">これらのしきい値を構成するには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="59c41-107">You must have the dqs_administrator role on the DQS_MAIN database to configure these threshold values.</span></span>  
  
##  <a name="configuring-the-threshold-values"></a><a name="Configure"></a><span data-ttu-id="59c41-108">しきい値の構成</span><span class="sxs-lookup"><span data-stu-id="59c41-108">Configuring the Threshold Values</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="59c41-109">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="59c41-109">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="59c41-110">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59c41-110">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="59c41-111">次に、[**全般設定**] タブをクリックします。このタブでは、クレンジングおよび照合アクティビティのしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="59c41-111">Next, click the **General Settings** tab. This tab enables you to specify threshold values for cleansing as well as matching activities.</span></span>  
  
4.  <span data-ttu-id="59c41-112">クレンジング アクティビティのしきい値を指定するには、 **[インタラクティブなクレンジング]** の下の次のボックスに適切な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="59c41-112">To specify threshold values for the cleansing activity, specify appropriate values in the following boxes under the **Interactive Cleansing** area:</span></span>  
  
    -   <span data-ttu-id="59c41-113">**[提案の最小スコア]**: コンピューター支援型のクレンジング プロセスの最中に、値の変更を提案するために DQS によって使用される最小スコア (信頼レベル) です。</span><span class="sxs-lookup"><span data-stu-id="59c41-113">**Min score for suggestions**: The minimum score or the confidence level that will be used by DQS for suggesting replacements for a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="59c41-114">割合値に相当する値を 10 進数表記で入力します。</span><span class="sxs-lookup"><span data-stu-id="59c41-114">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="59c41-115">たとえば、75% であれば「0.75」と入力します。</span><span class="sxs-lookup"><span data-stu-id="59c41-115">For example, type 0.75 for 75%.</span></span> <span data-ttu-id="59c41-116">この値は **[自動修正の最小スコア]** ボックスに指定した値以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="59c41-116">This value should be less than or equal to the value specified in the **Min score for auto corrections** box.</span></span> <span data-ttu-id="59c41-117">既定値は 0.7 です。</span><span class="sxs-lookup"><span data-stu-id="59c41-117">The default value is 0.7.</span></span>  
  
    -   <span data-ttu-id="59c41-118">**[自動修正の最小スコア]**: コンピューター支援型のクレンジング プロセスの最中に、値を自動修正するために DQS によって使用される最小スコア (信頼レベル) です。</span><span class="sxs-lookup"><span data-stu-id="59c41-118">**Min score for auto corrections**: The minimum score or the confidence level that will be used by DQS for automatically correcting a value during the computer-assisted cleansing process.</span></span> <span data-ttu-id="59c41-119">割合値に相当する値を 10 進数表記で入力します。</span><span class="sxs-lookup"><span data-stu-id="59c41-119">Enter a value in the decimal notation of the corresponding percentage value.</span></span> <span data-ttu-id="59c41-120">たとえば、90% であれば「0.9」と入力します。</span><span class="sxs-lookup"><span data-stu-id="59c41-120">For example, enter 0.9 for 90%.</span></span> <span data-ttu-id="59c41-121">既定値は 0.8 です。</span><span class="sxs-lookup"><span data-stu-id="59c41-121">The default value is 0.8.</span></span>  
  
5.  <span data-ttu-id="59c41-122">照合アクティビティのしきい値を指定するには、 **[照合]** の下の **[最小レコード スコア]** ボックスに適切な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="59c41-122">To specify threshold value for the matching activity, specify a value in the **Min record score** box under the **Matching** area.</span></span> <span data-ttu-id="59c41-123">この値は、あるレコードが別のレコードと一致すると見なされる最小スコアを表します。</span><span class="sxs-lookup"><span data-stu-id="59c41-123">This value signifies the minimum score for a record to be considered as a match for another record.</span></span> <span data-ttu-id="59c41-124">既定値は 80% です。</span><span class="sxs-lookup"><span data-stu-id="59c41-124">The default value is 80%.</span></span>  
  
6.  <span data-ttu-id="59c41-125">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59c41-125">Click **Close**.</span></span>  
  
  
