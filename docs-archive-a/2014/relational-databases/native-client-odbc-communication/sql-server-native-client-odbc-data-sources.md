---
title: SQL Server Native Client ODBC データソース |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6960118e13f0843640b18056bda655726cbbbd29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640906"
---
# <a name="sql-server-native-client-odbc-data-sources"></a><span data-ttu-id="83129-102">SQL Server Native Client ODBC データ ソース</span><span class="sxs-lookup"><span data-stu-id="83129-102">SQL Server Native Client ODBC Data Sources</span></span>
  <span data-ttu-id="83129-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソース名 (DSN) によって ODBC データ ソースが特定されます。ODBC データ ソースには、特定のサーバー上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続するために ODBC アプリケーションで必要となるすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="83129-103">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source name (DSN) identifies an ODBC data source containing all of the information that an ODBC application needs to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a specific server.</span></span> <span data-ttu-id="83129-104">ODBC データ ソース名を定義するには次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="83129-104">There are two ways you can define an ODBC data source name:</span></span>  
  
-   <span data-ttu-id="83129-105">クライアントコンピューターで、コントロールパネルの [管理ツール] を開き、[**データソース (ODBC)**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="83129-105">On a client computer, open Administrative Tools in Control Panel, and double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="83129-106">ODBC データ ソース アドミニストレーターが起動します。これを使用して DSN を作成できます。</span><span class="sxs-lookup"><span data-stu-id="83129-106">This will open the ODBC Data Source Administrator, which you can use to create a DSN.</span></span>  
  
-   <span data-ttu-id="83129-107">ODBC アプリケーションで、 [Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="83129-107">In an ODBC application, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="83129-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソースには次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="83129-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source contains:</span></span>  
  
-   <span data-ttu-id="83129-109">データ ソースの名前です。</span><span class="sxs-lookup"><span data-stu-id="83129-109">The name of the data source.</span></span>  
  
-   <span data-ttu-id="83129-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスとの接続に必要な情報。</span><span class="sxs-lookup"><span data-stu-id="83129-110">Any information needed to connect to a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83129-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスで使用する既定のデータベース (省略可)。</span><span class="sxs-lookup"><span data-stu-id="83129-111">The default database to use on a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (optional).</span></span>  
  
-   <span data-ttu-id="83129-112">使用する ANSI オプション、パフォーマンス統計情報をログに記録するかどうかなどの設定 (省略可)。</span><span class="sxs-lookup"><span data-stu-id="83129-112">Settings such as which ANSI options to use, whether to log performance statistics, and so on (optional).</span></span>  
  
 <span data-ttu-id="83129-113">データ ソース経由で接続する場合、ODBC アプリケーションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="83129-113">An ODBC application is not required to connect through a data source.</span></span> <span data-ttu-id="83129-114">ただしアプリケーションでは、ドライバーが DSN から検出する接続情報と同じ情報を、ODBC 接続関数に対して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83129-114">However, the application must provide the same connectivity information to an ODBC connect function that the driver would otherwise find in a DSN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83129-115">参照</span><span class="sxs-lookup"><span data-stu-id="83129-115">See Also</span></span>  
 [<span data-ttu-id="83129-116">ODBC&#41;&#40;SQL Server との通信</span><span class="sxs-lookup"><span data-stu-id="83129-116">Communicating with SQL Server &#40;ODBC&#41;</span></span>](communicating-with-sql-server-odbc.md)  
  
  
