---
title: SMO 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 988eef214608399bc3ec483d9976c2f5d52acb2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741190"
---
# <a name="smo-connection-manager"></a><span data-ttu-id="34a36-102">SMO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="34a36-102">SMO Connection Manager</span></span>
  <span data-ttu-id="34a36-103">SMO 接続マネージャーを使用すると、パッケージは、SQL 管理オブジェクト (SMO) サーバーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="34a36-103">An SMO connection manager enables a package to connect to a SQL Management Object (SMO) server.</span></span> <span data-ttu-id="34a36-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる転送タスクでは、SMO 接続マネージャーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="34a36-104">The transfer tasks that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes use an SMO connection manager.</span></span> <span data-ttu-id="34a36-105">たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを転送するログイン転送タスクでは、SMO 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="34a36-105">For example, the Transfer Logins task that transfers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins uses an SMO connection manager.</span></span>  
  
 <span data-ttu-id="34a36-106">SMO 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に SMO 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="34a36-106">When you add an SMO connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="34a36-107">接続マネージャーの `ConnectionManagerType` プロパティは、`SMOServer` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34a36-107">The `ConnectionManagerType` property of the connection manager is set to `SMOServer`.</span></span>  
  
 <span data-ttu-id="34a36-108">SMO 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="34a36-108">You can configure an SMO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="34a36-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているサーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="34a36-109">Specify the name of a server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="34a36-110">サーバーに接続する認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="34a36-110">Select the authentication mode for connecting to the server.</span></span>  
  
## <a name="configuration-of-the-smo-connection-manager"></a><span data-ttu-id="34a36-111">SMO 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="34a36-111">Configuration of the SMO Connection Manager</span></span>  
 <span data-ttu-id="34a36-112">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="34a36-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="34a36-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [SMO 接続マネージャー エディター](../smo-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34a36-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMO Connection Manager Editor](../smo-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="34a36-114">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34a36-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a36-115">参照</span><span class="sxs-lookup"><span data-stu-id="34a36-115">See Also</span></span>  
 [<span data-ttu-id="34a36-116">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="34a36-116">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
