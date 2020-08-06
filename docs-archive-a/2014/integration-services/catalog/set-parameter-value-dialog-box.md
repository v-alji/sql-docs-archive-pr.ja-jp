---
title: '[パラメーター値の設定] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 637267603c66921a566ca0d2a3f49f6142cfd203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736667"
---
# <a name="set-parameter-value-dialog-box"></a><span data-ttu-id="a0faa-102">[パラメーター値の設定] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="a0faa-102">Set Parameter Value Dialog Box</span></span>
  <span data-ttu-id="a0faa-103">プロジェクトとパッケージのパラメーターと接続マネージャーのプロパティの値を設定するには、 **[パラメーター値の設定]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-103">Use the **Set Parameter Value** dialog box to set values for parameters and connection manager properties, for projects and packages.</span></span>  
  
 <span data-ttu-id="a0faa-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="a0faa-104">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="a0faa-105">[[パラメーター値の設定] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="a0faa-105">[Open the Set Parameter Value dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="a0faa-106">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="a0faa-106">Configure the options</span></span>](#option)  
  
##  <a name="open-the-set-parameter-value-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="a0faa-107">[パラメーター値の設定] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="a0faa-107">Open the Set Parameter Value dialog box</span></span>  
  
1.  <span data-ttu-id="a0faa-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="a0faa-109">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="a0faa-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="a0faa-110">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="a0faa-111">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="a0faa-112">パッケージまたはプロジェクトを右クリックして **[構成]** をクリックし、 **[パラメーター]** タブまたは **[接続マネージャー]** タブの参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0faa-112">Right-click a package or project, click **Configure**, and then click the ellipsis button in the **Parameters** tab or in the **Connection Managers** tab.</span></span>  
  
##  <a name="configure-the-options"></a><a name="option"></a> <span data-ttu-id="a0faa-113">オプションの構成</span><span class="sxs-lookup"><span data-stu-id="a0faa-113">Configure the options</span></span>  
 <span data-ttu-id="a0faa-114">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="a0faa-114">**Parameter**</span></span>  
 <span data-ttu-id="a0faa-115">パラメーター名を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-115">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="a0faa-116">**Type**</span><span class="sxs-lookup"><span data-stu-id="a0faa-116">**Type**</span></span>  
 <span data-ttu-id="a0faa-117">パラメーター値のデータ型を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-117">Lists the data type of the parameter value.</span></span>  
  
 <span data-ttu-id="a0faa-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="a0faa-118">**Description**</span></span>  
 <span data-ttu-id="a0faa-119">パラメーターのオプションの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-119">Shows an optional description for the parameter.</span></span>  
  
 <span data-ttu-id="a0faa-120">**値の編集**</span><span class="sxs-lookup"><span data-stu-id="a0faa-120">**Edit value**</span></span>  
 <span data-ttu-id="a0faa-121">パラメーター値を編集する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-121">Select this option to edit the parameter value.</span></span>  
  
 <span data-ttu-id="a0faa-122">**パッケージの既定値を使用する**</span><span class="sxs-lookup"><span data-stu-id="a0faa-122">**Use default value from package**</span></span>  
 <span data-ttu-id="a0faa-123">パッケージに保存されている既定のパラメーター値を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-123">Select this option to use the default parameter value stored in the package.</span></span>  
  
 <span data-ttu-id="a0faa-124">**環境変数を使用する**</span><span class="sxs-lookup"><span data-stu-id="a0faa-124">**Use environment variable**</span></span>  
 <span data-ttu-id="a0faa-125">環境に保存されている変数値を使用する場合に選択します。この変数値はプロジェクトまたはパッケージによって参照されます。</span><span class="sxs-lookup"><span data-stu-id="a0faa-125">Select this option to use a variable value stored in the environment, which is referenced by the project or package.</span></span> <span data-ttu-id="a0faa-126">環境参照をプロジェクトまたはパッケージに追加するには、 **[構成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0faa-126">To add an environment reference to a project or package, use the **Configure** dialog box.</span></span> <span data-ttu-id="a0faa-127">詳細については、「 [[構成] ダイアログ ボックス](configure-dialog-box.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0faa-127">For more information, see [Configure Dialog Box](configure-dialog-box.md).</span></span>  
  
  
