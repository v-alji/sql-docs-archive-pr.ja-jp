---
title: SQL Server Data Tools | でパッケージログ記録を有効にします。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641776"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a><span data-ttu-id="52bd1-102">SQL Server Data Tools でパッケージのログ記録を有効にする</span><span class="sxs-lookup"><span data-stu-id="52bd1-102">Enable Package Logging in SQL Server Data Tools</span></span>
  <span data-ttu-id="52bd1-103">この手順では、パッケージにログを追加し、パッケージ レベルのログ記録を構成し、ログ構成を XML ファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-103">This procedure describes how to add logs to a package, configure package-level logging, and save the logging configuration to an XML file.</span></span> <span data-ttu-id="52bd1-104">ログはパッケージ レベルでのみ追加できますが、パッケージに含まれるコンテナーでのログを有効にするためにパッケージでログ記録を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52bd1-104">You can add logs only at the package level, but the package does not have to perform logging to enable logging in the containers that the package includes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="52bd1-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置した場合、パッケージ実行に対して設定したログ記録レベルは、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用して構成したパッケージのログ記録レベルをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-105">If you deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the logging level that you set for the package execution overrides the package logging that you configure using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="52bd1-106">既定では、パッケージに含まれるコンテナーは、親コンテナーと同じログ構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-106">By default, the containers in the package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="52bd1-107">それぞれのコンテナーのログ オプションの設定については、「 [保存されている構成ファイルを使用してログ記録を構成する](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52bd1-107">For information about setting logging options for individual containers, see [Configure Logging by Using a Saved Configuration File](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).</span></span>  
  
### <a name="to-enable-logging-in-a-package"></a><span data-ttu-id="52bd1-108">パッケージ内でのログ記録を有効にするには</span><span class="sxs-lookup"><span data-stu-id="52bd1-108">To enable logging in a package</span></span>  
  
1.  <span data-ttu-id="52bd1-109">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="52bd1-109">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="52bd1-110">次に、 **[SSIS]** メニューの **[ログ記録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-110">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="52bd1-111">**[プロバイダーの種類]** 一覧からログ プロバイダーを選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-111">Select a log provider in the **Provider type** list, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="52bd1-112">**[構成]** 列で、接続マネージャーを選択するか、 **[\<New connection>]** をクリックして、このログ プロバイダーに適した種類の接続マネージャーを新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-112">In the **Configuration** column, select a connection manager or click **\<New connection>** to create a new connection manager of the appropriate type for the log provider.</span></span> <span data-ttu-id="52bd1-113">選択したプロバイダーに応じて、次のいずれかの接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-113">Depending on the selected provider, use one of the following connection managers:</span></span>  
  
    -   <span data-ttu-id="52bd1-114">テキスト ファイル用には、ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-114">For Text files, use a File connection manager.</span></span> <span data-ttu-id="52bd1-115">詳細については、「 [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="52bd1-115">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
    -   <span data-ttu-id="52bd1-116">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]用には、ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-116">For [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use a File connection manager.</span></span>  
  
    -   <span data-ttu-id="52bd1-117">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]用には、OLE DB 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-117">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use an OLE DB connection manager.</span></span> <span data-ttu-id="52bd1-118">詳細については、「 [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52bd1-118">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
    -   <span data-ttu-id="52bd1-119">Windows イベント ログ用には何も指定しません。</span><span class="sxs-lookup"><span data-stu-id="52bd1-119">For Windows Event Log, do nothing.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="52bd1-120">によってログが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="52bd1-120">automatically creates the log.</span></span>  
  
    -   <span data-ttu-id="52bd1-121">XML ファイル用には、ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-121">For XML files, use a File connection manager.</span></span>  
  
5.  <span data-ttu-id="52bd1-122">パッケージで使用するそれぞれのログについて、手順 3. ～ 4. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-122">Repeat steps 3 and 4 for each log to use in the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52bd1-123">パッケージでは、それぞれの種類で複数のログを使用できます。</span><span class="sxs-lookup"><span data-stu-id="52bd1-123">A package can use more than one log of each type.</span></span>  
  
6.  <span data-ttu-id="52bd1-124">必要に応じて、パッケージレベルのチェック ボックスをオンにします。次に、パッケージレベルのログ記録で使用するログを選択し、 **[詳細]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-124">Optionally, select the package-level check box, select the logs to use for package-level logging, and then click the **Details** tab.</span></span>  
  
7.  <span data-ttu-id="52bd1-125">**[詳細]** タブで、 **[イベント]** をオンにしてすべてのログ エントリのログを記録することを指定するか、または **[イベント]** をオフにしてイベントを個別に選択します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-125">On the **Details** tab, select **Events** to log all log entries, or clear **Events** to select individual events.</span></span>  
  
8.  <span data-ttu-id="52bd1-126">必要に応じて、 **[詳細設定]** をクリックし、ログに記録する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="52bd1-126">Optionally, click **Advanced** to specify which information to log.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52bd1-127">既定では、すべての情報がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="52bd1-127">By default, all information is logged.</span></span>  
  
9. <span data-ttu-id="52bd1-128">**[詳細]** タブで、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-128">On the **Details** tab, click **Save.**</span></span> <span data-ttu-id="52bd1-129">**[名前を付けて保存]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="52bd1-129">The **Save As** dialog box appears.</span></span> <span data-ttu-id="52bd1-130">ログ構成を保存するフォルダーに移動し、新しいログ構成のファイル名を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-130">Locate the folder in which to save the logging configuration, type a file name for the new log configuration, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="52bd1-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-131">Click **OK**.</span></span>  
  
11. <span data-ttu-id="52bd1-132">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52bd1-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bd1-133">参照</span><span class="sxs-lookup"><span data-stu-id="52bd1-133">See Also</span></span>  
 <span data-ttu-id="52bd1-134">[SSIS&#41; ログ &#40;Integration Services](performance/integration-services-ssis-logging.md) </span><span class="sxs-lookup"><span data-stu-id="52bd1-134">[Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md) </span></span>  
 [<span data-ttu-id="52bd1-135">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="52bd1-135">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
