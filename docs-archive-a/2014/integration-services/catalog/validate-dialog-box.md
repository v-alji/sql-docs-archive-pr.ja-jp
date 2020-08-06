---
title: '[検証] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69e29d106dc9f4f100bf191911c5c34e0250be8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632631"
---
# <a name="validate-dialog-box"></a><span data-ttu-id="35c3c-102">[検証] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="35c3c-102">Validate Dialog Box</span></span>
  <span data-ttu-id="35c3c-103">**のプロジェクトまたはパッケージの一般的な問題を確認するには、** [検証] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-103">Use the **Validate** dialog box to check for common problems in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a project or package.</span></span>  
  
 <span data-ttu-id="35c3c-104">問題がある場合は、ダイアログ ボックスの上部にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="35c3c-104">If there is a problem, a message is displayed at the top of the dialog box.</span></span> <span data-ttu-id="35c3c-105">それ以外の場合は、上部に "準備完了" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="35c3c-105">Otherwise, the term Ready displays at the top.</span></span>  
  
 <span data-ttu-id="35c3c-106">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="35c3c-106">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="35c3c-107">[[検証] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="35c3c-107">[Open the Validate dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="35c3c-108">[[全般] ページのオプションの設定](#general)</span><span class="sxs-lookup"><span data-stu-id="35c3c-108">[Set the options on the General page](#general)</span></span>  
  
##  <a name="open-the-validate-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="35c3c-109">[検証] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="35c3c-109">Open the Validate dialog box</span></span>  
  
1.  <span data-ttu-id="35c3c-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="35c3c-111">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="35c3c-111">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="35c3c-112">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-112">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="35c3c-113">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-113">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="35c3c-114">検証するプロジェクトまたはパッケージが格納されているフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-114">Expand the folder that contains the project or package you want to validate.</span></span>  
  
5.  <span data-ttu-id="35c3c-115">プロジェクトまたはパッケージを右クリックし、 **[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="35c3c-115">Right-click the package or package, and then click **Validate**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="35c3c-116">[全般] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="35c3c-116">Set the options on the General page</span></span>  
 <span data-ttu-id="35c3c-117">**Environment**</span><span class="sxs-lookup"><span data-stu-id="35c3c-117">**Environment**</span></span>  
 <span data-ttu-id="35c3c-118">プロジェクトまたはパッケージの検証に使用する環境を選択します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-118">Select the environment that you want to use to validate the project or package.</span></span>  
  
 <span data-ttu-id="35c3c-119">**32 ビット ランタイム**</span><span class="sxs-lookup"><span data-stu-id="35c3c-119">**32-bit runtime**</span></span>  
 <span data-ttu-id="35c3c-120">32 ビット ランタイムを使用してパッケージを実行する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-120">Select to use a 32-bit runtime to execute a package.</span></span>  
  
 <span data-ttu-id="35c3c-121">**[パラメーター]** タブには、プロジェクトまたはパッケージの検証に使用するパラメーターの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35c3c-121">The **Parameters** tab lists the parameter values that you use to validate the project or package.</span></span> <span data-ttu-id="35c3c-122">[パラメーター] タブのオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-122">The following are the options on the Parameters tab.</span></span>  
  
 <span data-ttu-id="35c3c-123">**コンテナー**</span><span class="sxs-lookup"><span data-stu-id="35c3c-123">**Container**</span></span>  
 <span data-ttu-id="35c3c-124">パラメーターを含むオブジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-124">Lists the object that contains the parameter.</span></span>  
  
 <span data-ttu-id="35c3c-125">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="35c3c-125">**Parameter**</span></span>  
 <span data-ttu-id="35c3c-126">パラメーターの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-126">Lists the name of the parameters</span></span>  
  
 <span data-ttu-id="35c3c-127">**Value**</span><span class="sxs-lookup"><span data-stu-id="35c3c-127">**Value**</span></span>  
 <span data-ttu-id="35c3c-128">パラメーター値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-128">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="35c3c-129">**[接続マネージャー]** タブには、プロジェクトまたはパッケージの検証に使用する接続マネージャーのプロパティ値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="35c3c-129">The **Connection Managers** tab lists the connection manager property values that you use to validate the project or package.</span></span>  
  
 <span data-ttu-id="35c3c-130">**[接続マネージャー]** タブのオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-130">The following are the options on the **Connection Managers** tab.</span></span>  
  
 <span data-ttu-id="35c3c-131">**コンテナー**</span><span class="sxs-lookup"><span data-stu-id="35c3c-131">**Container**</span></span>  
 <span data-ttu-id="35c3c-132">接続マネージャーを含むオブジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-132">Lists the object that contains the connection manager.</span></span>  
  
 <span data-ttu-id="35c3c-133">**Name**</span><span class="sxs-lookup"><span data-stu-id="35c3c-133">**Name**</span></span>  
 <span data-ttu-id="35c3c-134">接続マネージャーの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-134">Lists the connection manager name.</span></span>  
  
 <span data-ttu-id="35c3c-135">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="35c3c-135">**Property name**</span></span>  
 <span data-ttu-id="35c3c-136">接続マネージャーのプロパティの名前を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-136">Lists the name of the connection manager property.</span></span>  
  
 <span data-ttu-id="35c3c-137">**Value**</span><span class="sxs-lookup"><span data-stu-id="35c3c-137">**Value**</span></span>  
 <span data-ttu-id="35c3c-138">接続マネージャーのプロパティに割り当てられた値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3c-138">Lists the value assigned to the connection manager property.</span></span>  
  
  
