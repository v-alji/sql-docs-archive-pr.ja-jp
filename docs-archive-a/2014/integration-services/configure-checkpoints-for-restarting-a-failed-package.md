---
title: 失敗したパッケージを再起動するためのチェックポイントを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a85354377453e0b24692ab8c2b567cc8998b6b05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736661"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a><span data-ttu-id="15f78-102">失敗したパッケージを再開するためのチェックポイントを構成する</span><span class="sxs-lookup"><span data-stu-id="15f78-102">Configure Checkpoints for Restarting a Failed Package</span></span>
  <span data-ttu-id="15f78-103">パッケージ全体を再実行するのではなく、障害が発生した時点からパッケージを再開するように [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを構成するには、チェックポイントに適用するプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="15f78-103">You configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to restart from a point of failure, instead of rerunning the entire package, by setting the properties that apply to checkpoints.</span></span>  
  
### <a name="to-configure-a-package-to-restart"></a><span data-ttu-id="15f78-104">パッケージを再開するように構成するには</span><span class="sxs-lookup"><span data-stu-id="15f78-104">To configure a package to restart</span></span>  
  
1.  <span data-ttu-id="15f78-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、構成するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="15f78-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to configure.</span></span>  
  
2.  <span data-ttu-id="15f78-106">**ソリューション エクスプローラー**で、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="15f78-106">In **Solution Explorer**, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="15f78-107">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="15f78-107">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="15f78-108">制御フローのデザイン画面の背景で任意の場所を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15f78-108">Right-click anywhere in the background of the control flow design surface, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="15f78-109">SaveCheckpoints プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="15f78-109">Set the SaveCheckpoints property to `True`.</span></span>  
  
6.  <span data-ttu-id="15f78-110">CheckpointFileName プロパティにチェックポイント ファイルの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="15f78-110">Type the name of the checkpoint file in the CheckpointFileName property.</span></span>  
  
7.  <span data-ttu-id="15f78-111">CheckpointUsage プロパティを、次の 2 つの値のどちらかに設定します。</span><span class="sxs-lookup"><span data-stu-id="15f78-111">Set the CheckpointUsage property to one of two values:</span></span>  
  
    -   <span data-ttu-id="15f78-112">チェックポイントから常にパッケージを再開するには、`Always` を選択します。</span><span class="sxs-lookup"><span data-stu-id="15f78-112">Select `Always` to always restart the package from the checkpoint.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="15f78-113">チェックポイント ファイルが使用できない場合はエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="15f78-113">An error occurs if the checkpoint file is not available.</span></span>  
  
    -   <span data-ttu-id="15f78-114">チェックポイント ファイルが使用できる場合のみパッケージを再開するには、`IfExists` を選択します。</span><span class="sxs-lookup"><span data-stu-id="15f78-114">Select `IfExists` to restart the package only if the checkpoint file is available.</span></span>  
  
8.  <span data-ttu-id="15f78-115">パッケージが再開できる地点のタスクおよびコンテナーを構成します。</span><span class="sxs-lookup"><span data-stu-id="15f78-115">Configure the tasks and containers from which the package can restart.</span></span>  
  
    -   <span data-ttu-id="15f78-116">タスクまたはコンテナーを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="15f78-116">Right-click a task or container and click **Properties**.</span></span>  
  
    -   <span data-ttu-id="15f78-117">`True`選択した各タスクおよびコンテナーに対して、FailPackageOnFailure プロパティをに設定します。</span><span class="sxs-lookup"><span data-stu-id="15f78-117">Set the FailPackageOnFailure property to `True` for each selected task and container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f78-118">参照</span><span class="sxs-lookup"><span data-stu-id="15f78-118">See Also</span></span>  
 [<span data-ttu-id="15f78-119">チェックポイントを使用してパッケージを再開する</span><span class="sxs-lookup"><span data-stu-id="15f78-119">Restart Packages by Using Checkpoints</span></span>](packages/restart-packages-by-using-checkpoints.md)  
  
  
