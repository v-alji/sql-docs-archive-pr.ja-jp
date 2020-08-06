---
title: FTP 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a402f399ba4b7e69fc1d3cbca9dd64b32217ced1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713398"
---
# <a name="ftp-connection-manager"></a><span data-ttu-id="1412c-102">FTP 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="1412c-102">FTP Connection Manager</span></span>
  <span data-ttu-id="1412c-103">FTP 接続マネージャーを使用すると、パッケージは、ファイル転送プロトコル (FTP) サーバーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="1412c-103">An FTP connection manager enables a package to connect to a File Transfer Protocol (FTP) server.</span></span> <span data-ttu-id="1412c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる FTP タスクでは、この接続マネージャーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1412c-104">The FTP task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="1412c-105">FTP 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に FTP 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="1412c-105">When you add an FTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that can be resolved as an FTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="1412c-106">接続マネージャーの `ConnectionManagerType` プロパティは、`FTP` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1412c-106">The `ConnectionManagerType` property of the connection manager is set to `FTP`.</span></span>  
  
 <span data-ttu-id="1412c-107">FTP 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="1412c-107">You can configure the FTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="1412c-108">サーバー名とサーバー ポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="1412c-108">Specify a server name and server port.</span></span>  
  
-   <span data-ttu-id="1412c-109">匿名アクセスを指定するか、または基本認証のユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1412c-109">Specify anonymous access, or provide a user name and a password for basic authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1412c-110">FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1412c-110">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="1412c-111">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1412c-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="1412c-112">タイムアウト、再試行回数、および一度にコピーするデータ量を指定します。</span><span class="sxs-lookup"><span data-stu-id="1412c-112">Set the time-out, number of retries, and the amount of data to copy at a time.</span></span>  
  
-   <span data-ttu-id="1412c-113">FTP 接続マネージャーでパッシブ モードを使用するか、アクティブ モードを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1412c-113">Indicate whether the FTP connection manager uses passive or active mode.</span></span>  
  
 <span data-ttu-id="1412c-114">FTP 接続マネージャーの接続先である FTP サイトの構成によっては、接続マネージャーの次の既定値の変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1412c-114">Depending on the configuration of the FTP site to which the FTP connection manager connects, you may need to change the following default values of the connection manager:</span></span>  
  
-   <span data-ttu-id="1412c-115">サーバー ポートは 21 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1412c-115">The server port is set to 21.</span></span> <span data-ttu-id="1412c-116">FTP サイトがリッスンするポートを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1412c-116">You should specify the port that the FTP site listens to.</span></span>  
  
-   <span data-ttu-id="1412c-117">ユーザー名は "anonymous" に設定されています。</span><span class="sxs-lookup"><span data-stu-id="1412c-117">The user name is set to "anonymous".</span></span> <span data-ttu-id="1412c-118">FTP サイトで必要になる資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1412c-118">You should provide the credentials that the FTP site requires.</span></span>  
  
## <a name="activepassive-modes"></a><span data-ttu-id="1412c-119">アクティブ/パッシブ モード</span><span class="sxs-lookup"><span data-stu-id="1412c-119">Active/Passive Modes</span></span>  
 <span data-ttu-id="1412c-120">FTP 接続マネージャーは、アクティブ モードまたはパッシブ モードのどちらかを使用して、ファイルを送受信できます。</span><span class="sxs-lookup"><span data-stu-id="1412c-120">An FTP connection manager can send and receive files using either active mode or passive mode.</span></span> <span data-ttu-id="1412c-121">アクティブ モードでは、サーバーがデータ接続を開始し、パッシブ モードでは、クライアントがデータ接続を開始します。</span><span class="sxs-lookup"><span data-stu-id="1412c-121">In active mode, the server initiates the data connection, and in passive mode, the client initiates the data connection.</span></span>  
  
## <a name="configuration-of-the-ftp-connection-manager"></a><span data-ttu-id="1412c-122">FTP 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="1412c-122">Configuration of the FTP Connection Manager</span></span>  
 <span data-ttu-id="1412c-123">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="1412c-123">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1412c-124">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティについては、「 [[FTP 接続マネージャー エディター]](../ftp-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1412c-124">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [FTP Connection Manager Editor](../ftp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="1412c-125">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1412c-125">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1412c-126">参照</span><span class="sxs-lookup"><span data-stu-id="1412c-126">See Also</span></span>  
 <span data-ttu-id="1412c-127">[FTP タスク](../control-flow/ftp-task.md) </span><span class="sxs-lookup"><span data-stu-id="1412c-127">[FTP Task](../control-flow/ftp-task.md) </span></span>  
 [<span data-ttu-id="1412c-128">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="1412c-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
