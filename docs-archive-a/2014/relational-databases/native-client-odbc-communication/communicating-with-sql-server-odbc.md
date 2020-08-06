---
title: SQL Server との通信 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: rothja
ms.author: jroth
ms.openlocfilehash: c41ac2dcce9c5bdbdd351148d16bcaa8f067d22f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738370"
---
# <a name="communicating-with-sql-server-odbc"></a><span data-ttu-id="10b6d-102">SQL Server との通信 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="10b6d-102">Communicating with SQL Server (ODBC)</span></span>
  <span data-ttu-id="10b6d-103">ODBC アプリケーションがのインスタンスと通信するには [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、環境ハンドルと接続ハンドルを割り当て、データソースに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10b6d-103">For an ODBC application to communicate with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it must allocate environment and connection handles and connect to the data source.</span></span> <span data-ttu-id="10b6d-104">接続が確立されると、アプリケーションからサーバーにクエリを送信し、任意の結果セットを処理できます。</span><span class="sxs-lookup"><span data-stu-id="10b6d-104">After a connection is established, the application can send queries to the server and process any result sets.</span></span> <span data-ttu-id="10b6d-105">データ ソースの使用が終了したら、アプリケーションでデータ ソースを切断して接続ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="10b6d-105">When the application has finished using the data source, it disconnects from the data source and frees the connection handle.</span></span> <span data-ttu-id="10b6d-106">すべての接続ハンドルを解放してから、環境ハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="10b6d-106">When the application has freed all its connection handles, it frees the environment handle.</span></span>  
  
 <span data-ttu-id="10b6d-107">アプリケーションからは任意の数のデータ ソースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="10b6d-107">An application can connect to any number of data sources.</span></span> <span data-ttu-id="10b6d-108">また、アプリケーションでは、複数のドライバーと複数のデータ ソースの組み合わせ、1 つのドライバーと複数データ ソースの組み合わせ、1 つのドライバーと 1 つのデータ ソースへの複数の接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="10b6d-108">The application can use a combination of drivers and data sources, the same driver and a combination of data sources, or even the same driver and multiple connections to the same data source.</span></span>  
  
 <span data-ttu-id="10b6d-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC サンプルは、MSDN の[SQL Server ダウンロード](https://go.microsoft.com/fwlink/?LinkId=62796)ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="10b6d-109">You can download [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC samples from the [SQL Server Downloads](https://go.microsoft.com/fwlink/?LinkId=62796) page on MSDN.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10b6d-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="10b6d-110">In This Section</span></span>  
  
-   [<span data-ttu-id="10b6d-111">環境ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="10b6d-111">Allocating an Environment Handle</span></span>](allocating-an-environment-handle.md)  
  
-   [<span data-ttu-id="10b6d-112">接続ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="10b6d-112">Allocating a Connection Handle</span></span>](allocating-a-connection-handle.md)  
  
-   [<span data-ttu-id="10b6d-113">SQL Server Native Client ODBC データ ソース</span><span class="sxs-lookup"><span data-stu-id="10b6d-113">SQL Server Native Client ODBC Data Sources</span></span>](../../integration-services/connection-manager/data-sources.md)  
  
-   [<span data-ttu-id="10b6d-114">ODBC&#41;&#40;データソースへの接続</span><span class="sxs-lookup"><span data-stu-id="10b6d-114">Connecting to a Data Source &#40;ODBC&#41;</span></span>](connecting-to-a-data-source-odbc.md)  
  
-   [<span data-ttu-id="10b6d-115">データ ソースからの切断</span><span class="sxs-lookup"><span data-stu-id="10b6d-115">Disconnecting from a Data Source</span></span>](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="10b6d-116">参照</span><span class="sxs-lookup"><span data-stu-id="10b6d-116">See Also</span></span>  
 <span data-ttu-id="10b6d-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="10b6d-117">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="10b6d-118">SQLSetEnvAttr</span><span class="sxs-lookup"><span data-stu-id="10b6d-118">SQLSetEnvAttr</span></span>](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
