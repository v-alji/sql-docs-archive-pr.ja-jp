---
title: SAP BW 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 06b166a1-a9df-48ea-a0e8-9b8d6979c0a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc3bb32c4895c6ec8fbcf31d57e8685c74de32dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633269"
---
# <a name="sap-bw-connection-manager"></a><span data-ttu-id="85349-102">SAP BW 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="85349-102">SAP BW Connection Manager</span></span>
  <span data-ttu-id="85349-103">SAP BW 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の接続マネージャー コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="85349-103">The SAP BW connection manager is the connection manager component of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="85349-104">したがって、SAP BW 接続マネージャーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の変換元と変換先コンポーネントが必要とする SAP Netweaver BW version 7 システムへの接続を提供します</span><span class="sxs-lookup"><span data-stu-id="85349-104">Thus, the SAP BW connection manager provides the connectivity to an SAP Netweaver BW version 7 system that the source and destination components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW need.</span></span> <span data-ttu-id="85349-105">( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW パッケージの一部の SAP BW 変換元と変換先は、SAP BW 接続マネージャーを使用する唯一の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントです)。</span><span class="sxs-lookup"><span data-stu-id="85349-105">(The SAP BW source and destination that are part of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW package are the only [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that use the SAP BW connection manager.)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="85349-106">Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="85349-106">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="85349-107">SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85349-107">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
 <span data-ttu-id="85349-108">SAP BW 接続マネージャーをパッケージに追加する場合、接続マネージャーの `ConnectionManagerType` プロパティを `SAPBI` に設定します。</span><span class="sxs-lookup"><span data-stu-id="85349-108">When you add an SAP BW connection manager to a package, the `ConnectionManagerType` property of the connection manager is set to `SAPBI`.</span></span>  
  
## <a name="configuring-the-sap-bw-connection-manager"></a><span data-ttu-id="85349-109">SAP BW 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="85349-109">Configuring the SAP BW Connection Manager</span></span>  
 <span data-ttu-id="85349-110">SAP BW 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="85349-110">You can configure the SAP BW connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="85349-111">接続のクライアント、ユーザー名、パスワード、および言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="85349-111">Provide the client, user name, password, and language for the connection.</span></span>  
  
-   <span data-ttu-id="85349-112">1 つのアプリケーション サーバーまたは負荷分散されたサーバーのグループに接続するかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="85349-112">Choose whether to connect to a single application server or to a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="85349-113">単一のアプリケーション サーバーのホストとシステム数を指定するか、負荷分散されたサーバー グループのメッセージ サーバー、グループ、および SID を指定します。</span><span class="sxs-lookup"><span data-stu-id="85349-113">Provide the host and system number for a single application server, or provide the message server, group, and SID for a group of load-balanced servers.</span></span>  
  
-   <span data-ttu-id="85349-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW のコンポーネントに対する RFC 関数呼び出しのカスタム ログを有効にします</span><span class="sxs-lookup"><span data-stu-id="85349-114">Enable custom logging of RFC function calls for the components of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW.</span></span> <span data-ttu-id="85349-115">(このログは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで有効にできる、省略可能なログとは異なります)。RFC 関数呼び出しのログを有効にするには、RFC の各関数呼び出しの前後に作成されるログ ファイルを格納するディレクトリを指定します</span><span class="sxs-lookup"><span data-stu-id="85349-115">(This logging is separate from the optional logging that you can enable on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.) To enable logging of RFC function calls, you specify a directory in which to store the log files that are created before and after each RFC function call.</span></span> <span data-ttu-id="85349-116">(このログ機能は、XML 形式で多くのログ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="85349-116">(This logging feature creates many log files in XML format.</span></span> <span data-ttu-id="85349-117">これらのログ ファイルには転送されるデータのすべての行も含まれるため、大量のディスク領域を消費する可能性があります)。ログ ディレクトリを選択しないと、ログ記録は有効になりません。</span><span class="sxs-lookup"><span data-stu-id="85349-117">As these log files also contain all the rows of data that are transferred, these log files may consume a large amount of disk space.) If you do not select a log directory, logging is not enabled.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="85349-118">転送されるデータに機密情報が含まれている場合、ログ ファイルには機密情報も含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="85349-118">If the data that is transferred contains sensitive information, the log files will also contain that sensitive information.</span></span>  
  
-   <span data-ttu-id="85349-119">入力した値を使用して接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="85349-119">Use the values that you have entered to test the connection.</span></span>  
  
 <span data-ttu-id="85349-120">接続マネージャーを構成するために必要な値がわからない場合は、SAP 管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="85349-120">If you do not know all the values that are required to configure the connection manager, you might have to ask your SAP administrator.</span></span>  
  
 <span data-ttu-id="85349-121">SAP BW 接続マネージャー、変換元、変換先の構成および使用方法の詳細については、ホワイト ペーパー「 [SAP BI 7.0 を使用した SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85349-121">For a walkthrough that demonstrates how to configure and use the SAP BW connection manager, source, and destination, see the white paper, [Using SQL Server 2008 Integration Services with SAP BI 7.0](https://go.microsoft.com/fwlink/?LinkID=137090).</span></span> <span data-ttu-id="85349-122">このホワイト ペーパーには、SAP BW で必要なオブジェクトの構成方法についても説明されています。</span><span class="sxs-lookup"><span data-stu-id="85349-122">This white paper also shows how to configure the required objects in SAP BW.</span></span>  
  
### <a name="using-the-ssis-designer-to-configure-the-source"></a><span data-ttu-id="85349-123">SSIS デザイナーを使用してソースを構成する</span><span class="sxs-lookup"><span data-stu-id="85349-123">Using the SSIS Designer to Configure the Source</span></span>  
 <span data-ttu-id="85349-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できる、SAP BW マネージャーのプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85349-124">For more information about the properties of the SAP BW connection manager that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="85349-125">SAP BW 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="85349-125">SAP BW Connection Manager Editor</span></span>](../sap-bw-connection-manager-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="85349-126">参照</span><span class="sxs-lookup"><span data-stu-id="85349-126">See Also</span></span>  
 [<span data-ttu-id="85349-127">Microsoft Connector 1.1 for SAP BW のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="85349-127">Microsoft Connector 1.1 for SAP BW Components</span></span>](../microsoft-connector-for-sap-bw-components.md)  
  
  
