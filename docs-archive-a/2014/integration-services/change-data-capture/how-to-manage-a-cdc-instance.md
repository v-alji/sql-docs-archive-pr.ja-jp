---
title: CDC インスタンスを管理する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e387b9e1a75b7279a68d1c9c9b637f5473071013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712286"
---
# <a name="how-to-manage-a-cdc-instance"></a><span data-ttu-id="ef1d5-102">How to Manage a CDC Instance</span><span class="sxs-lookup"><span data-stu-id="ef1d5-102">How to Manage a CDC Instance</span></span>
  <span data-ttu-id="ef1d5-103">この手順では、CDC デザイナー コンソールを使用して CDC インスタンスの操作を実行時に管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-103">This procedure describes how to use the CDC Designer Console to manage CDC instance operations at runtime.</span></span>  
  
### <a name="to-manage-cdc-instance-operations"></a><span data-ttu-id="ef1d5-104">CDC インスタンスの操作を管理するには</span><span class="sxs-lookup"><span data-stu-id="ef1d5-104">To manage CDC instance operations</span></span>  
  
1.  <span data-ttu-id="ef1d5-105">**[スタート]** メニューの **[CDC デザイナー コンソール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="ef1d5-106">左側のペインで **[Change Data Capture]** を展開し、表示するインスタンスが含まれているサービスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="ef1d5-107">操作するインスタンスの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-107">Select the name of an instance you want to work with.</span></span>  
  
4.  <span data-ttu-id="ef1d5-108">CDC デザイナー コンソールの右側にある **[アクション]** ペインで、実行する操作をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-108">From the **Actions** pane on the right side of the CDC Designer Console, click on the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="ef1d5-109">左ペインでインスタンスの名前を右クリックして、実行する操作を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-109">You can also right-click the name of the instance in the left pane and select the operation you want to carry out.</span></span>  
  
     <span data-ttu-id="ef1d5-110">実行できるタスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-110">You can carry out the following tasks:</span></span>  
  
    -   <span data-ttu-id="ef1d5-111">**[開始]** : 変更のキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-111">**Start**: To start capturing changes.</span></span>  
  
    -   <span data-ttu-id="ef1d5-112">**[停止]** : 変更のキャプチャを停止します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-112">**Stop**: To stop capturing changes</span></span>  
  
    -   <span data-ttu-id="ef1d5-113">**[リセット]** : CDC インスタンスを初期 (空) の状態にリセットするには、 **[リセット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-113">**Reset**: Click **Reset** to reset the CDC instance to its initial (empty) state.</span></span> <span data-ttu-id="ef1d5-114">このオプションは、CDC インスタンスが停止しているときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-114">This option is available when the CDC instance is stopped.</span></span> <span data-ttu-id="ef1d5-115">変更テーブル内のすべての変更および CDC インスタンスの内部状態が削除されます。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-115">All changes in the change tables and the CDC instance internal state are deleted.</span></span> <span data-ttu-id="ef1d5-116">CDC インスタンスが後から開始されると、変更キャプチャはその時点から開始され、CDC インスタンスの開始後に開始されたトランザクションのみがキャプチャの対象となります。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-116">When the CDC instance is started later on, change capture will start from that point in time and only includes transactions that started after the CDC instance started.</span></span>  
  
    -   <span data-ttu-id="ef1d5-117">**[削除]** : CDC インスタンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-117">**Delete**: To delete the CDC instance.</span></span>  
  
    -   <span data-ttu-id="ef1d5-118">**[Oracle ログ スクリプト]** : [Oracle ログ スクリプト] ダイアログ ボックスに Oracle 補足ログ スクリプトを表示するには、 **[Oracle ログ スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-118">**Oracle Logging Script**: Click **Oracle Logging Script** to display the Oracle Logging script dialog box with the Oracle supplemental-logging script.</span></span> <span data-ttu-id="ef1d5-119">このダイアログ ボックスで実行できる操作の詳細については、「 [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-119">For information on what you can do in this dialog box, see [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).</span></span>  
  
         <span data-ttu-id="ef1d5-120">**注**: 補足ログ スクリプトを実行すると、[スクリプトを実行するための Oracle 資格情報] ダイアログ ボックスが表示されます。このダイアログ ボックスで、有効な Oracle ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-120">**Note**: When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="ef1d5-121">適切な Oracle 資格情報を指定する方法については、「 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-121">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
    -   <span data-ttu-id="ef1d5-122">**[CDC インスタンスの配置]** : CDC インスタンスの配置スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-122">**CDC Instance Deployment**: To generate a deployment script for the CDC Instance.</span></span> <span data-ttu-id="ef1d5-123">このダイアログ ボックスの詳細については、「 [CDC Instance Deployment Script](cdc-instance-deployment-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-123">For information about this dialog box, see [CDC Instance Deployment Script](cdc-instance-deployment-script.md).</span></span>  
  
     <span data-ttu-id="ef1d5-124">これらの作業の詳細については、「 [Manage a CDC Instance](manage-a-cdc-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-124">For more information about these tasks, see [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
 <span data-ttu-id="ef1d5-125">**[プロパティ]** を選択して、CDC インスタンスの構成プロパティを編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-125">You can also select **Properties** to edit the CDC instance configuration properties.</span></span> <span data-ttu-id="ef1d5-126">CDC インスタンスのプロパティの編集の詳細については、「 [Edit Instance Properties](edit-instance-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef1d5-126">For more information about editing the CDC instance properties, see [Edit Instance Properties](edit-instance-properties.md).</span></span>  
  
  
