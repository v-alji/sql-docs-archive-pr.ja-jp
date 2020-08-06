---
title: SQL Server Compact Edition 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Compact, connection manager
- connections [Integration Services], SQL Server Compact
- connection managers [Integration Services], SQL Server Compact
ms.assetid: ba627d4d-41f4-49fc-a921-f534cde67770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d4feb001cc7c0fd0bd8b6e60d5ab22b33ad2eb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741186"
---
# <a name="sql-server-compact-edition-connection-manager"></a><span data-ttu-id="376df-102">SQL Server Compact Edition 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="376df-102">SQL Server Compact Edition Connection Manager</span></span>
  <span data-ttu-id="376df-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 接続マネージャーを使用すると、パッケージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="376df-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager enables a package to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span> <span data-ttu-id="376df-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に含まれる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact 変換先では、この接続マネージャーの使用により、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベース内のテーブルに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="376df-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager to load data into a table in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="376df-105">64 ビット コンピューターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データ ソースに接続するパッケージを 32 ビット モードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="376df-105">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="376df-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact データ ソースへの接続に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider は、32 ビット版でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="376df-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
## <a name="configuration-the-sql-server-compact-edition-connection-manager"></a><span data-ttu-id="376df-107">SQL Server Compact Edition 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="376df-107">Configuration the SQL Server Compact Edition Connection Manager</span></span>  
 <span data-ttu-id="376df-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Compact 接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時にコンパクトな接続を解決する接続マネージャーを作成し、接続マネージャーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。</span><span class="sxs-lookup"><span data-stu-id="376df-108">When you add a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="376df-109">接続マネージャーの `ConnectionManagerType` プロパティは、`SQLMOBILE` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="376df-109">The `ConnectionManagerType` property of the connection manager is set to `SQLMOBILE`.</span></span>  
  
 <span data-ttu-id="376df-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="376df-110">You can configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="376df-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベースの場所を指定する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="376df-111">Provide a connection string that specifies the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact database.</span></span>  
  
-   <span data-ttu-id="376df-112">パスワードで保護されているデータベースのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="376df-112">Provide a password for a password-protected database.</span></span>  
  
-   <span data-ttu-id="376df-113">データベースが格納されるサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="376df-113">Specify the server on which the database is stored.</span></span>  
  
-   <span data-ttu-id="376df-114">接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="376df-114">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="376df-115">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="376df-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="376df-116">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="376df-116">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="376df-117">[[SQL Server Compact Edition 接続マネージャー エディター] &#40;[接続] ページ&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)</span><span class="sxs-lookup"><span data-stu-id="376df-117">[SQL Server Compact Edition Connection Manager Editor &#40;Connection Page&#41;](../sql-server-compact-edition-connection-manager-editor-connection-page.md)</span></span>  
  
-   <span data-ttu-id="376df-118">[[SQL Server Compact Edition 接続マネージャー エディター] &#40;[すべて] ページ&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)</span><span class="sxs-lookup"><span data-stu-id="376df-118">[SQL Server Compact Edition Connection Manager Editor &#40;All Page&#41;](../sql-server-compact-edition-connection-manager-editor-all-page.md)</span></span>  
  
 <span data-ttu-id="376df-119">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="376df-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
