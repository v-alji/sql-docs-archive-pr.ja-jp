---
title: SAP BW 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec970319-e749-4753-8675-9cf76ed99669
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 527af979fc9c92062f24e1fe161b93e88ed4ab4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714510"
---
# <a name="sap-bw-connection-manager-editor"></a><span data-ttu-id="f0171-102">SAP BW 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="f0171-102">SAP BW Connection Manager Editor</span></span>
  <span data-ttu-id="f0171-103">SAP Netweaver BW Version 7 システムへの接続に使用するプロパティを指定するには、 **[SAP BW 接続マネージャー エディター]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0171-103">Use the **SAP BW Connection Manager Editor** to specify the properties to use to connect to an SAP Netweaver BW version 7 system.</span></span>  
  
 <span data-ttu-id="f0171-104">SAP BW 接続マネージャーは、SAP Netweaver BW Version 7 システムに SAP BW 変換元または変換先を接続します。</span><span class="sxs-lookup"><span data-stu-id="f0171-104">The SAP BW connection manager provides connectivity to an SAP Netweaver BW 7 system for use by the SAP BW source or destination.</span></span> <span data-ttu-id="f0171-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 接続マネージャーの詳細については、「 [SAP BW 接続マネージャー](connection-manager/sap-bw-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0171-105">To learn more about the SAP BW connection manager of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, see [SAP BW Connection Manager](connection-manager/sap-bw-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f0171-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f0171-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="f0171-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0171-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="f0171-108">**SAP BW 接続マネージャー エディターを開くには**</span><span class="sxs-lookup"><span data-stu-id="f0171-108">**To open the SAP BW Connection Manager Editor**</span></span>  
  
1.  <span data-ttu-id="f0171-109">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、SAP BW 接続マネージャーが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="f0171-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that contains the SAP BW connection manager.</span></span>  
  
2.  <span data-ttu-id="f0171-110">**[制御フロー]** タブ上にある [接続マネージャー] 領域で、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f0171-110">In the Connection Managers area on the **Control Flow** tab, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="f0171-111">[SAP BW 接続マネージャー] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0171-111">Double-click the SAP BW connection manager.</span></span>  
  
         <span data-ttu-id="f0171-112">または</span><span class="sxs-lookup"><span data-stu-id="f0171-112">-or-</span></span>  
  
    -   <span data-ttu-id="f0171-113">[SAP BW 接続マネージャー] を右クリックし、 **[編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0171-113">Right-click the SAP BW connection manager, and then select **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0171-114">Options</span><span class="sxs-lookup"><span data-stu-id="f0171-114">Options</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-115">接続マネージャーを構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="f0171-115">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="f0171-116">**Client**</span><span class="sxs-lookup"><span data-stu-id="f0171-116">**Client**</span></span>  
 <span data-ttu-id="f0171-117">システムのクライアント数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-117">Specify the client number of the system.</span></span>  
  
 <span data-ttu-id="f0171-118">**Language**</span><span class="sxs-lookup"><span data-stu-id="f0171-118">**Language**</span></span>  
 <span data-ttu-id="f0171-119">システムが使用する言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-119">Specify the language that the system uses.</span></span> <span data-ttu-id="f0171-120">たとえば、英語の場合は、 **[EN]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-120">For example, specify **EN** for English.</span></span>  
  
 <span data-ttu-id="f0171-121">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="f0171-121">**User name**</span></span>  
 <span data-ttu-id="f0171-122">システムへの接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-122">Specify the user name that will be used to connect to the system.</span></span>  
  
 <span data-ttu-id="f0171-123">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="f0171-123">**Password**</span></span>  
 <span data-ttu-id="f0171-124">そのユーザー名のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-124">Specify the password that will be used with the user name.</span></span>  
  
 <span data-ttu-id="f0171-125">**単一のアプリケーション サーバーを使用する**</span><span class="sxs-lookup"><span data-stu-id="f0171-125">**Use single application server**</span></span>  
 <span data-ttu-id="f0171-126">単一のアプリケーション サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="f0171-126">Connect to a single application server.</span></span>  
  
 <span data-ttu-id="f0171-127">負荷分散されたサーバーのグループに接続するには、 **[負荷分散を使用する]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f0171-127">To connect to a group of load-balanced servers, use the **Use load balancing** option instead.</span></span>  
  
 <span data-ttu-id="f0171-128">**Host**</span><span class="sxs-lookup"><span data-stu-id="f0171-128">**Host**</span></span>  
 <span data-ttu-id="f0171-129">単一のアプリケーション サーバーに接続する場合、ホスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-129">If connecting to a single application server, specify the host name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-130">このオプションは、 **[単一のアプリケーション サーバーを使用する]** オプションを選択している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0171-130">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="f0171-131">**システム数**</span><span class="sxs-lookup"><span data-stu-id="f0171-131">**System number**</span></span>  
 <span data-ttu-id="f0171-132">単一のアプリケーション サーバーに接続する場合、システム数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-132">If connecting to a single application server, specify the system number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-133">このオプションは、 **[単一のアプリケーション サーバーを使用する]** オプションを選択している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0171-133">This option is only available if you have selected the **Use single application server** option.</span></span>  
  
 <span data-ttu-id="f0171-134">**[負荷分散を使用する]**</span><span class="sxs-lookup"><span data-stu-id="f0171-134">**Use load balancing**</span></span>  
 <span data-ttu-id="f0171-135">負荷分散されたサーバーのグループに接続します。</span><span class="sxs-lookup"><span data-stu-id="f0171-135">Connect to a group of load-balanced servers.</span></span>  
  
 <span data-ttu-id="f0171-136">単一のアプリケーション サーバーに接続するには、 **[単一のアプリケーション サーバーを使用する]** オプションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="f0171-136">To connect to a single application server, use the **Use single application server** option instead.</span></span>  
  
 <span data-ttu-id="f0171-137">**メッセージ サーバー**</span><span class="sxs-lookup"><span data-stu-id="f0171-137">**Message server**</span></span>  
 <span data-ttu-id="f0171-138">負荷分散されたサーバーのグループに接続する場合は、メッセージ サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-138">If connecting to a group of load-balanced servers, specify the name of the message server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-139">このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0171-139">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="f0171-140">**グループ**</span><span class="sxs-lookup"><span data-stu-id="f0171-140">**Group**</span></span>  
 <span data-ttu-id="f0171-141">負荷分散されたサーバーのグループに接続する場合は、サーバー グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-141">If connecting to a group of load-balanced servers, specify the name of the server group name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-142">このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0171-142">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="f0171-143">**SID**</span><span class="sxs-lookup"><span data-stu-id="f0171-143">**SID**</span></span>  
 <span data-ttu-id="f0171-144">負荷分散されたサーバーのグループに接続する場合は、接続のシステム ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0171-144">If connecting to a group of load-balanced servers, specify the System ID for the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0171-145">このオプションは、 **[負荷分散を使用する]** オプションを選択している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0171-145">This option is only available if you have selected the **Use load balancing** option.</span></span>  
  
 <span data-ttu-id="f0171-146">**ログ ディレクトリ**</span><span class="sxs-lookup"><span data-stu-id="f0171-146">**Log directory**</span></span>  
 <span data-ttu-id="f0171-147">[!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW のコンポーネントに対するログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0171-147">Enable logging for the components of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span>  
  
 <span data-ttu-id="f0171-148">ログを有効にするには、RFC の各関数呼び出しの前後に作成されたログ ファイルのディレクトリを指定します</span><span class="sxs-lookup"><span data-stu-id="f0171-148">To enable logging, specify a directory for the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="f0171-149">(このログ機能は、XML 形式で多くのログ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0171-149">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="f0171-150">これらのログ ファイルには転送されるデータのすべての行も含まれるため、大量のディスク領域を消費する可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="f0171-150">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f0171-151">転送されるデータに機密情報が含まれている場合、ログ ファイルには機密情報も含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="f0171-151">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
 <span data-ttu-id="f0171-152">ログ ディレクトリを指定するには、ディレクトリ パスに手動で入力するか、 **[参照]** をクリックし、ログ ディレクトリを参照します。</span><span class="sxs-lookup"><span data-stu-id="f0171-152">To specify the log directory, you can either enter the directory path manually, or click **Browse** and browse to the log directory.</span></span>  
  
 <span data-ttu-id="f0171-153">ログ ディレクトリを選択しないと、ログ記録は有効になりません。</span><span class="sxs-lookup"><span data-stu-id="f0171-153">If you do not select a log directory, logging is not enabled.</span></span>  
  
 <span data-ttu-id="f0171-154">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="f0171-154">**Browse**</span></span>  
 <span data-ttu-id="f0171-155">ログ ディレクトリのフォルダーを参照して選択します。</span><span class="sxs-lookup"><span data-stu-id="f0171-155">Browse to select a folder for the log directory.</span></span>  
  
 <span data-ttu-id="f0171-156">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="f0171-156">**Test Connection**</span></span>  
 <span data-ttu-id="f0171-157">指定した値を使用して接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="f0171-157">Test the connection using the values that you have provided.</span></span> <span data-ttu-id="f0171-158">**[接続テスト]** をクリックすると、接続が成功または失敗したかを示すメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0171-158">After clicking **Test Connection**, a message box appears and indicates whether the connection succeeded or failed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0171-159">参照</span><span class="sxs-lookup"><span data-stu-id="f0171-159">See Also</span></span>  
 [<span data-ttu-id="f0171-160">Microsoft Connector 1.1 for SAP BW の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="f0171-160">Microsoft Connector 1.1 for SAP BW F1 Help</span></span>](microsoft-connector-for-sap-bw-f1-help.md)  
  
  
