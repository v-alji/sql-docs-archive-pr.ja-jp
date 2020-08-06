---
title: 接続ハンドルを割り当てる |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, passwords
- ODBC applications, connections
- handles [SQL Server Native Client]
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- SQL Server Native Client ODBC driver, connection handles
- connection handles [SQL Server Native Client]
- modifying passwords
- SQLAllocHandle function
ms.assetid: 471d8a31-199c-4f92-bb10-004fc7733b35
author: rothja
ms.author: jroth
ms.openlocfilehash: d3cf84e541f114d527d9a00cd19bce705a09af30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742034"
---
# <a name="allocating-a-connection-handle"></a><span data-ttu-id="df946-102">接続ハンドルの割り当て</span><span class="sxs-lookup"><span data-stu-id="df946-102">Allocating a Connection Handle</span></span>
  <span data-ttu-id="df946-103">アプリケーションからデータ ソースまたはドライバーに接続する前に、接続ハンドルを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="df946-103">Before the application can connect to a data source or driver, it must allocate a connection handle.</span></span> <span data-ttu-id="df946-104">これを行うには、 *Handletype*パラメーターを SQL_HANDLE_DBC に設定し、初期化された環境ハンドルを指すように*InputHandle*を指定して、 **SQLAllocHandle**を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="df946-104">This is done by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_DBC and *InputHandle* pointing to an initialized environment handle.</span></span>  
  
 <span data-ttu-id="df946-105">接続の特性は、接続属性の設定により制御されます。</span><span class="sxs-lookup"><span data-stu-id="df946-105">The characteristics of the connection are controlled by setting connection attributes.</span></span> <span data-ttu-id="df946-106">たとえば、トランザクションは接続レベルで行われるので、トランザクション分離レベルは 1 つの接続属性になります。</span><span class="sxs-lookup"><span data-stu-id="df946-106">For example, because transactions occur at the connection level, the transaction isolation level is a connection attribute.</span></span> <span data-ttu-id="df946-107">同様に、ログイン タイムアウト、つまり接続試行がタイムアウトするまで待機する秒数も接続属性です。</span><span class="sxs-lookup"><span data-stu-id="df946-107">Similarly, the login time-out, or number of seconds to wait while trying to connect before timing out, is a connection attribute.</span></span>  
  
 <span data-ttu-id="df946-108">接続属性は[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)で設定され、その現在の設定は[Sqlgetconnectattr](../native-client-odbc-api/sqlgetconnectattr.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="df946-108">Connection attributes are set with [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md), and their current settings are retrieved with [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md).</span></span> <span data-ttu-id="df946-109">接続を試行する前に**SQLSetConnectAttr**を呼び出すと、ODBC ドライバーマネージャーによって、接続構造に属性が格納され、接続プロセスの一部としてドライバー内に設定されます。</span><span class="sxs-lookup"><span data-stu-id="df946-109">If **SQLSetConnectAttr** is called before a connection is attempted, the ODBC Driver Manager stores the attributes in its connection structure and sets them in the driver as part of the connection process.</span></span> <span data-ttu-id="df946-110">接続属性の中には、アプリケーションが接続を試行する前に設定しなければならないものも、接続の確立後に設定できるものもあります。</span><span class="sxs-lookup"><span data-stu-id="df946-110">Some connection attributes must be set before the application attempts to connect; others can be set after the connection has completed.</span></span> <span data-ttu-id="df946-111">たとえば、SQL_ATTR_ODBC_CURSORS は接続前に設定する必要がありますが、SQL_ATTR_AUTOCOMMIT は接続後に設定できます。</span><span class="sxs-lookup"><span data-stu-id="df946-111">For example, SQL_ATTR_ODBC_CURSORS must be set before a connection is made, but SQL_ATTR_AUTOCOMMIT can be set after connecting.</span></span>  
  
 <span data-ttu-id="df946-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降に対してアプリケーションを実行している場合、表形式のデータ ストリーム (TDS) のネットワーク パケット サイズを再設定すると、パフォーマンスが向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="df946-112">Applications running against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 or later can sometimes improve their performance by resetting the tabular data stream (TDS) network packet size.</span></span> <span data-ttu-id="df946-113">サーバーに設定されている既定のパケット サイズは 4 KB です。</span><span class="sxs-lookup"><span data-stu-id="df946-113">The default packet size is set at the server, at 4 KB.</span></span> <span data-ttu-id="df946-114">パフォーマンスが最も高くなるのは、通常、パケット サイズが 4 ～ 8 KB のときです。</span><span class="sxs-lookup"><span data-stu-id="df946-114">A packet size of 4 KB to 8 KB generally gives the best performance.</span></span> <span data-ttu-id="df946-115">テストにより、他のパケット サイズの方がパフォーマンスが高くなることがわかった場合、アプリケーションではパケット サイズを再設定できます。</span><span class="sxs-lookup"><span data-stu-id="df946-115">If testing shows that it performs better with a different packet size, the application can reset the packet size.</span></span> <span data-ttu-id="df946-116">ODBC アプリケーションは、SQL_ATTR_PACKET_SIZE オプションを指定して**SQLSetConnectAttr**を呼び出すことによって接続する前にこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="df946-116">ODBC applications can do this before connecting by calling **SQLSetConnectAttr** with the SQL_ATTR_PACKET_SIZE option.</span></span> <span data-ttu-id="df946-117">パケット サイズを大きくすることでパフォーマンスが向上するアプリケーションもありますが、通常、8 KB を超えるパケット サイズを指定して向上するパフォーマンスはごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="df946-117">Some applications perform better with a larger packet size, but performance improvements are generally minimal for packet sizes larger than 8 KB.</span></span>  
  
 <span data-ttu-id="df946-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーには、アプリケーションが機能を向上させるために使用できる拡張接続属性が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="df946-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver has a number of extended connection attributes that an application can use to increase its functionality.</span></span> <span data-ttu-id="df946-119">これらの属性の一部は、データ ソースで指定可能なオプションと同じものをコントロールし、データ ソースで設定されたオプションをどれでもオーバーライドするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="df946-119">Some of these attributes control the same options that can be specified in data sources and used to override whatever option is set in a data source.</span></span> <span data-ttu-id="df946-120">たとえば、アプリケーションで引用符で囲まれた識別子を使用する場合は、ドライバー固有の属性である SQL_COPT_SS_QUOTED_IDENT を SQL_QI_ON に設定すると、データ ソースの設定とは関係なく、識別子を引用符で囲むというオプションが常に有効になります。</span><span class="sxs-lookup"><span data-stu-id="df946-120">For example, if an application uses quoted identifiers, it can set the driver-specific attribute SQL_COPT_SS_QUOTED_IDENT to SQL_QI_ON to ensure this option is always set regardless of the setting in any data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df946-121">参照</span><span class="sxs-lookup"><span data-stu-id="df946-121">See Also</span></span>  
 [<span data-ttu-id="df946-122">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="df946-122">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
