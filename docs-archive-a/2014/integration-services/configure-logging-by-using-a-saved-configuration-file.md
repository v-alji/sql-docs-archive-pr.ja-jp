---
title: 保存した構成ファイルを使用したログ記録の構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8eb517462d9e932906f739678fbd46c1004fb84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642236"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a><span data-ttu-id="5b072-102">保存されている構成ファイルを使用してログ記録を構成する</span><span class="sxs-lookup"><span data-stu-id="5b072-102">Configure Logging by Using a Saved Configuration File</span></span>
  <span data-ttu-id="5b072-103">この手順では、以前に保存したログ構成ファイルを読み込んでパッケージ内の新しいコンテナーのログ記録を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5b072-103">This procedure describes how to configure logging for new containers in a package by loading a previously saved logging configuration file.</span></span>  
  
 <span data-ttu-id="5b072-104">既定では、パッケージに含まれるすべてのコンテナーは、親コンテナーと同じログ構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b072-104">By default, all containers in a package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="5b072-105">たとえば、Foreach ループ内のタスクは、Foreach ループと同じログ構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b072-105">For example, the tasks in a Foreach Loop use the same logging configuration as the Foreach Loop.</span></span>  
  
### <a name="to-configure-logging-for-a-container"></a><span data-ttu-id="5b072-106">コンテナーのログ記録を構成するには</span><span class="sxs-lookup"><span data-stu-id="5b072-106">To configure logging for a container</span></span>  
  
1.  <span data-ttu-id="5b072-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5b072-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="5b072-108">次に、 **[SSIS]** メニューの **[ログ記録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b072-108">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="5b072-109">パッケージ ツリー ビューを展開し、構成するコンテナーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b072-109">Expand the package tree view and select the container to configure.</span></span>  
  
4.  <span data-ttu-id="5b072-110">**[プロバイダーとログ]** タブで、コンテナーに対して使用するログを選択します。</span><span class="sxs-lookup"><span data-stu-id="5b072-110">On the **Providers and Logs** tab, select the logs to use for the container.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b072-111">ログは、パッケージ レベルでのみ作成できます。</span><span class="sxs-lookup"><span data-stu-id="5b072-111">You can create logs only at the package level.</span></span> <span data-ttu-id="5b072-112">詳細については、「 [SQL Server Data Tools でパッケージのログ記録を有効にする](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b072-112">For more information, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
5.  <span data-ttu-id="5b072-113">**[詳細]** タブをクリックし、 **[読み込み]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b072-113">Click the **Details** tab and click **Load**.</span></span>  
  
6.  <span data-ttu-id="5b072-114">使用するログ構成ファイルを参照し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b072-114">Locate the logging configuration file you want to use and click **Open**.</span></span>  
  
7.  <span data-ttu-id="5b072-115">必要に応じて、 **[イベント]** 列のチェック ボックスをオンにして、ログ記録を行う異なるログ エントリを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b072-115">Optionally, select a different log entry to log by selecting its check box in the **Events** column.</span></span> <span data-ttu-id="5b072-116">**[詳細設定]** をクリックして、このエントリのログ記録を行うための情報の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="5b072-116">Click **Advanced** to select the type of information to log for this entry.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5b072-117">最初にログ構成を作成するときに使用されたコンテナーでは使用できない追加のログ エントリが新しいコンテナーに含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5b072-117">The new container may include additional log entries that are not available for the container originally used to create the logging configuration.</span></span> <span data-ttu-id="5b072-118">これらの追加のログ エントリをログに記録するには、手動で選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b072-118">These additional log entries must be selected manually if you want them to be logged.</span></span>  
  
8.  <span data-ttu-id="5b072-119">**[保存]** をクリックして、ログ構成の更新バージョンを保存します。</span><span class="sxs-lookup"><span data-stu-id="5b072-119">To save the updated version of the logging configuration, click **Save**.</span></span>  
  
9. <span data-ttu-id="5b072-120">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5b072-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b072-121">参照</span><span class="sxs-lookup"><span data-stu-id="5b072-121">See Also</span></span>  
 [<span data-ttu-id="5b072-122">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="5b072-122">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
