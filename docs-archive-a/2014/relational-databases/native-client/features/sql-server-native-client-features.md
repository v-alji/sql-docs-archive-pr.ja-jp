---
title: SQL Server Native Client の機能 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: rothja
ms.author: jroth
ms.openlocfilehash: bb4ba07f84848f754519f8f4fa1c3e56485e85a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633822"
---
# <a name="sql-server-native-client-features"></a><span data-ttu-id="ba35c-102">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="ba35c-102">SQL Server Native Client Features</span></span>
  <span data-ttu-id="ba35c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client では、Windows Data Access Components (WDAC、以前の Microsoft Data Access Components) の機能を公開するだけでなく、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の機能を公開するための機能が数多く実装されています。</span><span class="sxs-lookup"><span data-stu-id="ba35c-103">In addition to exposing features of the Windows (formerly Microsoft) Data Access Components (WDAC), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client also implements many other features to expose [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba35c-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ba35c-104">In This Section</span></span>  
 [<span data-ttu-id="ba35c-105">文字変換処理での ODBC ドライバーの動作の変更</span><span class="sxs-lookup"><span data-stu-id="ba35c-105">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 <span data-ttu-id="ba35c-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client で変更された動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-106">Discusses a change of behavior beginning in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span></span>  
  
 [<span data-ttu-id="ba35c-107">データベース ミラーリングの使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-107">Using Database Mirroring</span></span>](using-database-mirroring.md)  
 <span data-ttu-id="ba35c-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client がミラー化されたデータベースの使用をサポートするしくみについて説明します。これは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] スタンバイサーバー上のデータベースのコピー (ミラー) を保持する機能です。</span><span class="sxs-lookup"><span data-stu-id="ba35c-108">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the use of mirrored databases, which is the ability to keep a copy, or mirror, of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database on a standby server.</span></span>  
  
 [<span data-ttu-id="ba35c-109">非同期操作の実行</span><span class="sxs-lookup"><span data-stu-id="ba35c-109">Performing Asynchronous Operations</span></span>](performing-asynchronous-operations.md)  
 <span data-ttu-id="ba35c-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で、非同期操作をサポートする方法について説明します。非同期操作では、呼び出し側のスレッドをブロックせずに直ちに操作を戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="ba35c-110">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports asynchronous operations, which is the ability to return immediately without blocking on the calling thread.</span></span>  
  
 [<span data-ttu-id="ba35c-111">複数のアクティブな結果セット &#40;MARS&#41; の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-111">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](using-multiple-active-result-sets-mars.md)  
 <span data-ttu-id="ba35c-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client が複数のアクティブな結果セット (MARS) をサポートするしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-112">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports multiple active result sets (MARS).</span></span> <span data-ttu-id="ba35c-113">MARS では、単一のデータベース接続を使用して、複数の結果セットを実行したり受け取ったりできます。</span><span class="sxs-lookup"><span data-stu-id="ba35c-113">MARS enables you to execute and receive multiple result sets using a single database connection</span></span>  
  
 [<span data-ttu-id="ba35c-114">XML データ型の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-114">Using XML Data Types</span></span>](using-xml-data-types.md)  
 <span data-ttu-id="ba35c-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で XML データ型をサポートする方法について説明します。XML データ型とは、XML ベースのデータ型で、列の型、変数の型、パラメーターの型、または関数の戻り値の型として使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba35c-115">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the XML data type, which is a XML-based data type that can be used as a column type, variable type, parameter type, or function return type.</span></span>  
  
 [<span data-ttu-id="ba35c-116">ユーザー定義型の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-116">Using User-Defined Types</span></span>](using-user-defined-types.md)  
 <span data-ttu-id="ba35c-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client がユーザー定義型 (UDT) をサポートする方法について説明します。 UDT を使用すると、オブジェクトやカスタムデータ構造をデータベースに格納できるため、SQL 型システムが拡張され [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ba35c-117">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports User-Defined Types (UDT), which extends the SQL type system by allowing you to store objects and custom data structures in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="ba35c-118">大きな値をとるデータ型の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-118">Using Large Value Types</span></span>](using-large-value-types.md)  
 <span data-ttu-id="ba35c-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で大きな値のデータ型をサポートする方法について説明します。大きな値のデータ型とは、ラージ オブジェクト (LOB) データ型のことです。</span><span class="sxs-lookup"><span data-stu-id="ba35c-119">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports large value data types, which are large object data types (LOB).</span></span>  
  
 [<span data-ttu-id="ba35c-120">プログラムによるパスワードの変更</span><span class="sxs-lookup"><span data-stu-id="ba35c-120">Changing Passwords Programmatically</span></span>](changing-passwords-programmatically.md)  
 <span data-ttu-id="ba35c-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で、有効期限が切れたパスワードの処理をサポートする方法について説明します。この処理により、管理者の手を煩わせることなく、クライアント側でパスワードを変更できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ba35c-121">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the handling of expired passwords so that passwords can now be changed on the client without administrator involvement.</span></span>  
  
 [<span data-ttu-id="ba35c-122">スナップショット分離の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-122">Working with Snapshot Isolation</span></span>](working-with-snapshot-isolation.md)  
 <span data-ttu-id="ba35c-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で、行のバージョン管理の機能強化をサポートする方法について説明します。この機能強化では、リーダーとライターとの間で発生するブロックを回避することにより、データベースのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-123">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the enhancement to row versioning that improves database performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 [<span data-ttu-id="ba35c-124">クエリ通知の操作</span><span class="sxs-lookup"><span data-stu-id="ba35c-124">Working with Query Notifications</span></span>](working-with-query-notifications.md)  
 <span data-ttu-id="ba35c-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で、行セット変更時のコンシューマーへの通知をサポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-125">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports consumer notification on rowset modification.</span></span>  
  
 [<span data-ttu-id="ba35c-126">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="ba35c-126">Performing Bulk Copy Operations</span></span>](performing-bulk-copy-operations.md)  
 <span data-ttu-id="ba35c-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client が、テーブルまたはビューとの間で大量のデータを転送できるようにする一括コピー操作をどのようにサポートするかについて説明し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ba35c-127">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports bulk copy operations that allow the transfer of large amounts of data into or out of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 [<span data-ttu-id="ba35c-128">検証を伴わない暗号化の使用</span><span class="sxs-lookup"><span data-stu-id="ba35c-128">Using Encryption Without Validation</span></span>](using-encryption-without-validation.md)  
 <span data-ttu-id="ba35c-129">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用して、証明書の検証をせずに、サーバーに送信されるデータを暗号化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-129">Discusses how to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to encrypt data sent to the server without validating the certificate.</span></span>  
  
 [<span data-ttu-id="ba35c-130">テーブル値パラメーター &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="ba35c-130">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](table-valued-parameters-sql-server-native-client.md)  
 <span data-ttu-id="ba35c-131">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client によるテーブル値パラメーターのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-131">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the table-valued parameters.</span></span>  
  
 [<span data-ttu-id="ba35c-132">大きな CLR ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="ba35c-132">Large CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="ba35c-133">大きな共通言語ランタイム (CLR) ユーザー定義型 (UDT) のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-133">Discusses support for large common language runtime (CLR) user-defined types (UDTs).</span></span>  
  
 [<span data-ttu-id="ba35c-134">FILESTREAM のサポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-134">FILESTREAM Support</span></span>](filestream-support.md)  
 <span data-ttu-id="ba35c-135">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client による拡張 FILESTREAM 機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-135">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the enhanced FILESTREAM feature.</span></span>  
  
 [<span data-ttu-id="ba35c-136">クライアント接続でのサービス プリンシパル名 &#40;SPN&#41; のサポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-136">Service Principal Name &#40;SPN&#41; Support in Client Connections</span></span>](service-principal-name-spn-support-in-client-connections.md)  
 <span data-ttu-id="ba35c-137">あらゆるプロトコルでの相互認証を可能にする、サービス プリンシパル名 (SPN) のサポート強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-137">Discusses how support for service principal names (SPNs) has been extended to enable mutual authentication across all protocols.</span></span>  
  
 [<span data-ttu-id="ba35c-138">SQL Server Native Client におけるスパース列のサポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-138">Sparse Columns Support in SQL Server Native Client</span></span>](sparse-columns-support-in-sql-server-native-client.md)  
 <span data-ttu-id="ba35c-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client によるスパース列のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-139">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for sparse columns.</span></span>  
  
 [<span data-ttu-id="ba35c-140">日付と時刻の機能強化</span><span class="sxs-lookup"><span data-stu-id="ba35c-140">Date and Time Improvements</span></span>](date-and-time-improvements.md)  
 <span data-ttu-id="ba35c-141">日付と時刻のデータ型のために [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client に追加されたサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-141">Discusses support added to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the date and time data types.</span></span>  
  
 [<span data-ttu-id="ba35c-142">メタデータの検出</span><span class="sxs-lookup"><span data-stu-id="ba35c-142">Metadata Discovery</span></span>](metadata-discovery.md)  
 <span data-ttu-id="ba35c-143">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] で行われたメタデータ検出の機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-143">Discusses metadata discovery improvements that were made in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="ba35c-144">SQL Server Native Client 11.0 での UTF-16 のサポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-144">UTF-16 Support in SQL Server Native Client 11.0</span></span>](utf-16-support-in-sql-server-native-client-11-0.md)  
 <span data-ttu-id="ba35c-145">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] で導入された動作の変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-145">Discusses a behavior change introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="ba35c-146">列の結果または出力パラメーターをバインドするときに固定長バッファーを指定した場合、ターミネータ文字の前にバッファーに書き込まれる `wchar` 文字がサロゲート ペアの上位サロゲート コード ポイントである場合、および次の `wchar` 文字が下位サロゲート コード ポイントである場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲート コード ポイントを追加しません。</span><span class="sxs-lookup"><span data-stu-id="ba35c-146">If you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
 [<span data-ttu-id="ba35c-147">SQL Server Native Client の HADR サポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-147">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="ba35c-148">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] に追加された高可用性のディザスター リカバリー機能をアプリケーションで利用するための構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-148">Discusses how your application can be configured to take advantage of the high-availability, disaster recovery features added in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="ba35c-149">拡張イベント ログの診断情報へのアクセス</span><span class="sxs-lookup"><span data-stu-id="ba35c-149">Accessing Diagnostic Information in the Extended Events Log</span></span>](accessing-diagnostic-information-in-the-extended-events-log.md)  
 <span data-ttu-id="ba35c-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の機能強化とリング バッファーおよび XEvent ログの診断情報にアクセスできるデータ トレースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-150">Discusses enhancements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data tracing that gives you access to diagnostic information in the ring buffer and XEvents log.</span></span>  
  
 [<span data-ttu-id="ba35c-151">SQL Server Native Client における LocalDB のサポート</span><span class="sxs-lookup"><span data-stu-id="ba35c-151">SQL Server Native Client Support for LocalDB</span></span>](sql-server-native-client-support-for-localdb.md)  
 <span data-ttu-id="ba35c-152">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client による LocalDB 機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba35c-152">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the LocalDB feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba35c-153">参照</span><span class="sxs-lookup"><span data-stu-id="ba35c-153">See Also</span></span>  
 <span data-ttu-id="ba35c-154">[SQL Server Native Client プログラミング](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="ba35c-154">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="ba35c-155">[ODBC の操作方法に関するトピック](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="ba35c-155">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 <span data-ttu-id="ba35c-156">[OLE DB 方法に関するトピック](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="ba35c-156">[OLE DB How-to Topics](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span></span>  
 [<span data-ttu-id="ba35c-157">SQL Server Native Client のインストール</span><span class="sxs-lookup"><span data-stu-id="ba35c-157">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
