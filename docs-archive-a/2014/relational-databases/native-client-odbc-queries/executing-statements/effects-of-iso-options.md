---
title: ISO オプションの効果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 79deff1d77f4020aa7484629bac78d360ed7691f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631870"
---
# <a name="effects-of-iso-options"></a><span data-ttu-id="b2058-102">ISO オプションの効果</span><span class="sxs-lookup"><span data-stu-id="b2058-102">Effects of ISO Options</span></span>
  <span data-ttu-id="b2058-103">ODBC 標準は、ISO 標準と密接に対応しています。ODBC アプリケーションは、ODBC ドライバーの動作が標準に準拠していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b2058-103">The ODBC standard is closely matched to the ISO standard, and ODBC applications expect standard behavior from an ODBC driver.</span></span> <span data-ttu-id="b2058-104">ODBC 標準で定義されている動作よりも動作が厳密に一致するように、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、接続先の SQL Server のバージョンで使用可能な ISO オプションを常に使用します。</span><span class="sxs-lookup"><span data-stu-id="b2058-104">To make its behavior conform more closely with that defined in the ODBC standard, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver always uses any ISO options available in the version of SQL Server with which it connects.</span></span>  
  
 <span data-ttu-id="b2058-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーがのインスタンスに接続すると [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、サーバーは、クライアントが NATIVE client odbc ドライバーを使用していることを検出し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] いくつかのオプションをに設定します。</span><span class="sxs-lookup"><span data-stu-id="b2058-105">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server detects that the client is using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and sets several options on.</span></span>  
  
 <span data-ttu-id="b2058-106">ステートメント自体はドライバーが実行します。ODBC アプリケーションはステートメントの実行に対して何の要求も行いません。</span><span class="sxs-lookup"><span data-stu-id="b2058-106">The driver issues these statements itself; the ODBC application does nothing to request them.</span></span> <span data-ttu-id="b2058-107">ISO オプションを設定することで、SQL Native Client ODBC ドライバーを使用する ODBC アプリケーションの移植性が高まります。これは、サーバーの動作が ISO 標準に準拠するためです。</span><span class="sxs-lookup"><span data-stu-id="b2058-107">Setting these options allows ODBC applications using the driver to be more portable because the server behavior then matches the ISO standard.</span></span>  
  
 <span data-ttu-id="b2058-108">DB-Library ベースのアプリケーションは、通常これらのオプションを有効にしません。</span><span class="sxs-lookup"><span data-stu-id="b2058-108">DB-Library-based applications generally do not turn these options on.</span></span> <span data-ttu-id="b2058-109">ODBC または DB-LIBRARY クライアントが同じ SQL ステートメントを実行しているときに異なる動作を観察するサイトは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーの問題を指しているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b2058-109">Sites observing different behavior between ODBC or DB-Library clients when running the same SQL statement should not assume this points to a problem with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="b2058-110">最初に、Native Client ODBC ドライバーで使用されるのと同じ SET オプションを使用して、DB-LIBRARY 環境でステートメントを再実行する必要があり [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b2058-110">They should first rerun the statement in the DB-Library environment with the same SET options as would be used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="b2058-111">SET オプションはユーザーやアプリケーションがいつでも有効または無効にできるので、ストアド プロシージャやトリガーの開発者は、上記の SET オプションを有効にした場合と無効にした場合の両方で、開発したプロシージャやトリガーをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2058-111">Because SET options can be turned on and off at any time by users and applications, developers of stored procedures and triggers should also take care to test their procedures and triggers with the SET options listed above turned both on and off.</span></span> <span data-ttu-id="b2058-112">これにより、プロシージャやトリガーの起動時に、接続に設定されているオプションに関係なく、プロシージャやトリガーが適切に動作することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b2058-112">This ensures that the procedures and triggers work correctly regardless of which options a particular connection may have set on when they invoke the procedure or trigger.</span></span> <span data-ttu-id="b2058-113">これらのオプションのいずれかについて特定の設定が必要なトリガーやストアド プロシージャは、そのトリガーやストアド プロシージャの起動時に SET ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2058-113">Triggers or stored procedures that require a particular setting for one of these options should issue a SET statement at the start of the trigger or stored procedure.</span></span> <span data-ttu-id="b2058-114">この SET ステートメントは、トリガーやストアド プロシージャが実行されている間だけ有効になり、トリガーやストアド プロシージャが終了すると元の設定が復元されます。</span><span class="sxs-lookup"><span data-stu-id="b2058-114">This SET statement remains in effect only for the execution of the trigger or stored procedure; when the procedure or trigger ends, the original setting is restored.</span></span>  
  
 <span data-ttu-id="b2058-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続しているときは、4 番目の SET オプションの CONCAT_NULL_YIELDS_NULL も有効になります。</span><span class="sxs-lookup"><span data-stu-id="b2058-115">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a fourth SET option, CONCAT_NULL_YIELDS_NULL, is also set on.</span></span> <span data-ttu-id="b2058-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データソースに AnsiNPW = NO が指定されている場合、または[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)または[SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)のいずれかで、Native Client ODBC ドライバーでこれらのオプションが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="b2058-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not set these options on if AnsiNPW=NO is specified in the data source or on either [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) or [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).</span></span>  
  
 <span data-ttu-id="b2058-117">前に説明した ISO オプションと同様に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーでは、QuotedID = NO がデータソースで指定されている場合、または**SQLDriverConnect**または**SQLBrowseConnect**のいずれかで指定されている場合、QUOTED_IDENTIFIER オプションは有効になりません。</span><span class="sxs-lookup"><span data-stu-id="b2058-117">Like the ISO options noted earlier, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver does not turn the QUOTED_IDENTIFIER option on if QuotedID=NO is specified in the data source or on either **SQLDriverConnect** or **SQLBrowseConnect**.</span></span>  
  
 <span data-ttu-id="b2058-118">ドライバーが SET オプションの現在の状態を確認できるようにするために、ODBC アプリケーションでは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] SET ステートメントを使用して SET オプションを設定しないようにします。</span><span class="sxs-lookup"><span data-stu-id="b2058-118">To allow the driver to know the current state of SET options, ODBC applications should not use the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET statement to set these options.</span></span> <span data-ttu-id="b2058-119">これらのオプションを設定する場合は、データ ソースまたは接続オプションのみを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="b2058-119">They should only set these options using either the data source or the connection options.</span></span> <span data-ttu-id="b2058-120">アプリケーションが SET ステートメントを実行した場合、ドライバーは不正な SQL ステートメントを生成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b2058-120">If the application issues SET statements, the driver can generate incorrect SQL statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2058-121">参照</span><span class="sxs-lookup"><span data-stu-id="b2058-121">See Also</span></span>  
 <span data-ttu-id="b2058-122">[ODBC&#41;&#40;のステートメントの実行](executing-statements-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="b2058-122">[Executing Statements &#40;ODBC&#41;](executing-statements-odbc.md) </span></span>  
 <span data-ttu-id="b2058-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span><span class="sxs-lookup"><span data-stu-id="b2058-123">[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) </span></span>  
 [<span data-ttu-id="b2058-124">SQLBrowseConnect</span><span class="sxs-lookup"><span data-stu-id="b2058-124">SQLBrowseConnect</span></span>](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
