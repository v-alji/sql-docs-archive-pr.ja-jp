---
title: MSSQLSERVER_8992 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8992 (Database Engine error)
ms.assetid: 68467e6a-09d8-478f-8bd9-3bb09453ada3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: adcf914accab43202cf148fe852b334c9b078287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646158"
---
# <a name="mssqlserver_8992"></a><span data-ttu-id="23a5c-102">MSSQLSERVER_8992</span><span class="sxs-lookup"><span data-stu-id="23a5c-102">MSSQLSERVER_8992</span></span>
    
## <a name="details"></a><span data-ttu-id="23a5c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="23a5c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23a5c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="23a5c-104">Product Name</span></span>|<span data-ttu-id="23a5c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23a5c-105">SQL Server</span></span>|  
|<span data-ttu-id="23a5c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="23a5c-106">Event ID</span></span>|<span data-ttu-id="23a5c-107">8992</span><span class="sxs-lookup"><span data-stu-id="23a5c-107">8992</span></span>|  
|<span data-ttu-id="23a5c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="23a5c-108">Event Source</span></span>|<span data-ttu-id="23a5c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23a5c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23a5c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="23a5c-110">Component</span></span>|<span data-ttu-id="23a5c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23a5c-111">SQLEngine</span></span>|  
|<span data-ttu-id="23a5c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="23a5c-112">Symbolic Name</span></span>|<span data-ttu-id="23a5c-113">DBCC3_CHECK_CATALOG</span><span class="sxs-lookup"><span data-stu-id="23a5c-113">DBCC3_CHECK_CATALOG</span></span>|  
|<span data-ttu-id="23a5c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="23a5c-114">Message Text</span></span>|<span data-ttu-id="23a5c-115">カタログ メッセージ ERROR Level LEVEL の確認、状態 STATE:MESSAGE</span><span class="sxs-lookup"><span data-stu-id="23a5c-115">Check Catalog Msg ERROR Level LEVEL State STATE: MESSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23a5c-116">説明</span><span class="sxs-lookup"><span data-stu-id="23a5c-116">Explanation</span></span>  
 <span data-ttu-id="23a5c-117">DBCC CHECKCATALOG または DBCC CHECKDB により、指定されたオブジェクトの不整合がシステム メタデータ テーブルで検出されました。</span><span class="sxs-lookup"><span data-stu-id="23a5c-117">DBCC CHECKCATALOG or DBCC CHECKDB found an inconsistency in the system metadata tables for the specified object.</span></span> <span data-ttu-id="23a5c-118">つまり、記録されたオブジェクト ID とエラー メッセージで指定されたオブジェクトの間に不整合があります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-118">That is, there is an inconsistency between the recorded object ID and the object specified in error message.</span></span>  
  
 <span data-ttu-id="23a5c-119">このエラーは、システム メタデータに不整合が生じるような方法で 1 つ以上のシステム テーブルを手動で更新した場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-119">This error can occur when one or more system tables has been manually updated in a way that creates an inconsistency in the system metadata.</span></span> <span data-ttu-id="23a5c-120">たとえば、ユーザーが他のテーブルにある関連する行 (**sysindexes** や **syscolumns** など) を削除せずに、**sysobjects** テーブルからオブジェクトを手動で削除した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-120">For example, a user may have manually deleted an object from the **sysobjects** table without removing associated rows in other tables such as **sysindexes** and **syscolumns**.</span></span>  
  
 <span data-ttu-id="23a5c-121">このエラーは、SQL Server 2000 から SQL Server 2005 以降にアップグレードされたデータベースに対して DBCC CHECKDB を実行しているときに発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-121">This error can occur when running DBCC CHECKDB against a database that has been upgraded from SQL Server 2000 to SQL Server 2005 or later.</span></span> <span data-ttu-id="23a5c-122">SQL Server 2000 では、DBCC CHECKDB に DBCC CHECKCATALOG 機能がありませんでした。そのため、SQL Server 2000 のデータベースに対して DBCC CHECKCATALOG を指定して実行しない限り、アップグレード前にこのエラーはキャッチされません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-122">In SQL Server 2000, DBCC CHECKDB did not include DBCC CHECKCATALOG functionality, so the error would not be caught before upgrade unless DBCC CHECKCATALOG was specifically executed against the database in SQL Server 2000.</span></span>  
  
 <span data-ttu-id="23a5c-123">エラー 8992 と共に、次のいずれかのエラーが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-123">You may see any of the following errors in conjunction with error 8992:</span></span>  
  
 <span data-ttu-id="23a5c-124">メッセージ 3851 - システム テーブル sys.%ls%ls に無効な行 (%ls) が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="23a5c-124">Msg 3851 - An invalid row (%ls) was found in the system table sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-125">メッセージ 3852 - sys.%ls%ls の行 (%ls) と一致する行 (%ls) が sys.%ls%ls にありません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-125">Msg 3852 - Row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-126">3853 - sys.%ls%ls の行 (%ls) の属性 (%ls) には、sys.%ls%ls に一致する行 (%ls) がありません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-126">3853 - Attribute (%ls) of row (%ls) in sys.%ls%ls does not have a matching row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-127">3854 - 属性 (%ls) (sys.%ls%ls の行 (%ls)) には、sys.%ls%ls に一致する行 (%ls) がありますが、無効です。</span><span class="sxs-lookup"><span data-stu-id="23a5c-127">3854 - Attribute (%ls) of row (%ls) in sys.%ls%ls has a matching row (%ls) in sys.%ls%ls that is invalid.</span></span>  
  
 <span data-ttu-id="23a5c-128">3855 - 属性 (%ls) が存在しますが、sys.%ls%ls の行 (%ls) がありません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-128">3855 - Attribute (%ls) exists without a row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-129">3856 - 属性 (%ls) が存在しますが、sys.%ls%ls の行 (%ls) では使用できません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-129">3856 - Attribute (%ls) exists but should not for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-130">3857 - 属性 (%ls) が必要ですが、sys.%ls%ls の行 (%ls) にはありません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-130">3857 - The attribute (%ls) is required but is missing for row (%ls) in sys.%ls%ls.</span></span>  
  
 <span data-ttu-id="23a5c-131">3858 - sys.%ls%ls の行 (%ls) の属性 (%ls) には、無効な値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="23a5c-131">3858 - The attribute (%ls) of row (%ls) in sys.%ls%ls has an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23a5c-132">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="23a5c-132">User Action</span></span>  
  
### <a name="drop-and-re-create-the-specified-object"></a><span data-ttu-id="23a5c-133">指定されたオブジェクトを削除して再作成する</span><span class="sxs-lookup"><span data-stu-id="23a5c-133">Drop and Re-create the Specified Object</span></span>  
 <span data-ttu-id="23a5c-134">可能であれば、指定されたオブジェクトを削除して再作成します。</span><span class="sxs-lookup"><span data-stu-id="23a5c-134">If possible, drop and recreate the specified object.</span></span> <span data-ttu-id="23a5c-135">たとえば、オブジェクトがストアド プロシージャまたはユーザー定義型である場合、オブジェクトを再作成することで問題が解決する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-135">For example, if the object is a stored procedure or user-defined type, recreating the object may resolve the problem.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="23a5c-136">バックアップから復元する</span><span class="sxs-lookup"><span data-stu-id="23a5c-136">Restore from Backup</span></span>  
 <span data-ttu-id="23a5c-137">問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="23a5c-137">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span> <span data-ttu-id="23a5c-138">この操作は、バックアップにメタデータ エラーが含まれていない場合にのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="23a5c-138">This action is only applicable if the backup does not contain the metadata error.</span></span>  
  
### <a name="export-the-data-to-a-new-database"></a><span data-ttu-id="23a5c-139">新しいデータベースにデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="23a5c-139">Export the Data to a New Database</span></span>  
 <span data-ttu-id="23a5c-140">また、バックアップにメタデータの不整合が含まれている場合は、新しいデータベースを作成し、作成したデータベースに既存のデータベースのコンテンツをエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="23a5c-140">If the backup also contains the metadata inconsistency, you need to create a new database and export the contents of the existing database to the new database.</span></span>  
  
### <a name="dbcc-checkdb-cannot-repair-this-error"></a><span data-ttu-id="23a5c-141">DBCC CHECKDB でこのエラーを修復できない</span><span class="sxs-lookup"><span data-stu-id="23a5c-141">DBCC CHECKDB Cannot Repair This Error</span></span>  
 <span data-ttu-id="23a5c-142">このエラーを修正することはできません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-142">This error cannot be repaired.</span></span>  <span data-ttu-id="23a5c-143">バックアップからデータベースを復元できない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタマー サポート サービス (CSS) にご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="23a5c-143">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
### <a name="do-not-manually-update-system-tables"></a><span data-ttu-id="23a5c-144">システム テーブルを手動で更新しない</span><span class="sxs-lookup"><span data-stu-id="23a5c-144">Do Not Manually Update System Tables</span></span>  
 <span data-ttu-id="23a5c-145">システム テーブルは手動で更新しないでください。</span><span class="sxs-lookup"><span data-stu-id="23a5c-145">Do not make manual updates to system tables.</span></span> <span data-ttu-id="23a5c-146">SQL Server では、システム テーブルを手動で変更することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="23a5c-146">SQL Server does not support any manual changes to system databases.</span></span> <span data-ttu-id="23a5c-147">SQL Server データベース内のシステム テーブルを更新すると、2 つのイベント (イベント ID 17659 とイベント ID 3859) がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="23a5c-147">If you update a system table in a SQL Server database, two events (event ID 17659 and event ID 3859) are logged.</span></span> <span data-ttu-id="23a5c-148">詳細については、サポート技術情報の資料 2688307「SQL Server データベース内のシステム テーブルを更新するとイベント ID 17659 とイベント ID 3859 がログに記録される」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23a5c-148">For more information, see KB article 2688307, "Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a5c-149">参照</span><span class="sxs-lookup"><span data-stu-id="23a5c-149">See Also</span></span>  
 [<span data-ttu-id="23a5c-150">SQL Server データベース内のシステム テーブルを更新するとイベント ID 17659 とイベント ID 3859 がログに記録される</span><span class="sxs-lookup"><span data-stu-id="23a5c-150">Event ID 17659 and event ID 3859 are logged when you update system tables in a SQL Server database</span></span>](https://support.microsoft.com/kb/2688307/EN-US)  
  
  
