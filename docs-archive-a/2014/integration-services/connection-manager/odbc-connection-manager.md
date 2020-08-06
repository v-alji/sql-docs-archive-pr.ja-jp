---
title: ODBC 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1069e31f3f8ffaf14dde091d913ff6d9f8fa7cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639594"
---
# <a name="odbc-connection-manager"></a><span data-ttu-id="bd07f-102">ODBC 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="bd07f-102">ODBC Connection Manager</span></span>
  <span data-ttu-id="bd07f-103">ODBC 接続マネージャーを使用すると、パッケージは Open Database Connectivity (ODBC) の仕様を使用して、さまざまなデータベース管理システムに接続できます。</span><span class="sxs-lookup"><span data-stu-id="bd07f-103">An ODBC connection manager enables a package to connect to a variety of database management systems using the Open Database Connectivity specification (ODBC).</span></span>  
  
 <span data-ttu-id="bd07f-104">ODBC 接続をパッケージに追加し、接続マネージャーのプロパティを設定すると、は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 接続マネージャーを作成し、接続マネージャーを `Connections` パッケージのコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="bd07f-104">When you add an ODBC connection to a package and set the connection manager properties, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager and adds the connection manager to the `Connections` collection of the package.</span></span> <span data-ttu-id="bd07f-105">接続マネージャーは、実行時に物理 ODBC 接続として解決されます。</span><span class="sxs-lookup"><span data-stu-id="bd07f-105">At run time the connection manager is resolved as a physical ODBC connection.</span></span>  
  
 <span data-ttu-id="bd07f-106">接続マネージャーの `ConnectionManagerType` プロパティは、`ODBC` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd07f-106">The `ConnectionManagerType` property of the connection manager is set to `ODBC`.</span></span>  
  
 <span data-ttu-id="bd07f-107">ODBC 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="bd07f-107">You can configure the ODBC connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="bd07f-108">ユーザーまたはシステム データ ソースの名前を参照する、接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="bd07f-108">Provide a connection string that references a user or system data source name.</span></span>  
  
-   <span data-ttu-id="bd07f-109">接続先のサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="bd07f-109">Specify the server to connect to.</span></span>  
  
-   <span data-ttu-id="bd07f-110">接続を実行時に保持するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bd07f-110">Indicate whether the connection is retained at run time.</span></span>  
  
## <a name="configuration-of-the-odbc-connection-manager"></a><span data-ttu-id="bd07f-111">ODBC 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="bd07f-111">Configuration of the ODBC Connection Manager</span></span>  
 <span data-ttu-id="bd07f-112">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="bd07f-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="bd07f-113">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd07f-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="bd07f-114">ODBC 接続マネージャーの UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="bd07f-114">ODBC Connection Manager UI Reference</span></span>](../odbc-connection-manager-ui-reference.md)  
  
 <span data-ttu-id="bd07f-115">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bd07f-115">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd07f-116">参照</span><span class="sxs-lookup"><span data-stu-id="bd07f-116">See Also</span></span>  
 [<span data-ttu-id="bd07f-117">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="bd07f-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
