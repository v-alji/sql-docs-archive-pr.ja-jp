---
title: MSSQLSERVER_3168 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 764f456653365c085e9f756a749910bbd03b4259
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640986"
---
# <a name="mssqlserver_3168"></a><span data-ttu-id="6af2e-102">MSSQLSERVER_3168</span><span class="sxs-lookup"><span data-stu-id="6af2e-102">MSSQLSERVER_3168</span></span>
    
## <a name="details"></a><span data-ttu-id="6af2e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6af2e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6af2e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6af2e-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="6af2e-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6af2e-105">Event ID</span></span>|<span data-ttu-id="6af2e-106">3168</span><span class="sxs-lookup"><span data-stu-id="6af2e-106">3168</span></span>|  
|<span data-ttu-id="6af2e-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6af2e-107">Event Source</span></span>|<span data-ttu-id="6af2e-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6af2e-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6af2e-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6af2e-109">Component</span></span>|<span data-ttu-id="6af2e-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6af2e-110">SQLEngine</span></span>|  
|<span data-ttu-id="6af2e-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6af2e-111">Symbolic Name</span></span>|<span data-ttu-id="6af2e-112">LDDB_SYSTEMWRONGVER</span><span class="sxs-lookup"><span data-stu-id="6af2e-112">LDDB_SYSTEMWRONGVER</span></span>|  
|<span data-ttu-id="6af2e-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6af2e-113">Message Text</span></span>|<span data-ttu-id="6af2e-114">デバイス %ls のシステム データベースのバックアップは復元できません。このバックアップを作成したサーバーのバージョン (%ls) とこのサーバーのバージョン (%ls) が異なります。</span><span class="sxs-lookup"><span data-stu-id="6af2e-114">The backup of the system database on the device %ls cannot be restored because it was created by a different version of the server (%ls) than this server (%ls).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6af2e-115">説明</span><span class="sxs-lookup"><span data-stu-id="6af2e-115">Explanation</span></span>  
 <span data-ttu-id="6af2e-116">サーバーのビルドが最初のバックアップ実行時のビルドと異なる場合、システム データベース (**master**、**model**、**msdb**) のバックアップは復元できません。</span><span class="sxs-lookup"><span data-stu-id="6af2e-116">You cannot restore a backup of a system database (**master**, **model**, or **msdb**) on a server build that differs from the build on which the backup was originally performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6af2e-117">Service Pack または修正プログラムのビルドをインストールすると、サーバーのビルド番号は変更されます。サーバーのビルドは常に増分です。</span><span class="sxs-lookup"><span data-stu-id="6af2e-117">Installing a service pack or a hotfix build changes the server build number, and server builds are always incremental.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="6af2e-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="6af2e-118">Possible Causes</span></span>  
 <span data-ttu-id="6af2e-119">システム データベースのデータベース スキーマが、サーバー ビルド間で変更されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6af2e-119">The database schema for system databases may be changed across server builds.</span></span> <span data-ttu-id="6af2e-120">スキーマの変更によって一貫性が失われないようにするには、RESTORE ステートメントで、バックアップ ファイルのサーバー ビルド番号とバックアップを復元するサーバーのビルド番号を比較します。</span><span class="sxs-lookup"><span data-stu-id="6af2e-120">To make sure that a schema change does not cause inconsistencies, the RESTORE statement compares the server build number on the backup file to the build number of the server on which you are trying to restore the backup.</span></span> <span data-ttu-id="6af2e-121">ビルドが異なる場合、ステートメントでは 3168 のエラー メッセージが返され、復元操作は異常終了します。</span><span class="sxs-lookup"><span data-stu-id="6af2e-121">If the builds are different, the statement issues the 3168 error message, and the restore operation terminates abnormally.</span></span>  
  
 <span data-ttu-id="6af2e-122">たとえば、次のような場合にこの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="6af2e-122">Some scenarios in which this problem may occur include the following:</span></span>  
  
-   <span data-ttu-id="6af2e-123">サーバー A のシステム データベースを、サーバー B で行ったバックアップから復元しようとしており、サーバー A とサーバー B でサーバー ビルドが異なる。</span><span class="sxs-lookup"><span data-stu-id="6af2e-123">A user tries to restore a system database on Server A from a backup taken on Server B. Servers A and B are on different server builds.</span></span> <span data-ttu-id="6af2e-124">たとえば、サーバー A が最初のリリース バージョンのビルドで、サーバー B が Service Pack 1 (SP1) ビルドであるような場合です。</span><span class="sxs-lookup"><span data-stu-id="6af2e-124">For example, Server A might be on the original release version build and Server B might be on a service pack 1 (SP1) build.</span></span>  
  
-   <span data-ttu-id="6af2e-125">同じサーバーで行ったバックアップからシステム データベースを復元しようとしており、</span><span class="sxs-lookup"><span data-stu-id="6af2e-125">A user tries to restore a system database from a backup taken on the same server.</span></span> <span data-ttu-id="6af2e-126">バックアップ時にサーバーでは別のビルドを実行していた</span><span class="sxs-lookup"><span data-stu-id="6af2e-126">However, the server was running a different build when the backup occurred.</span></span> <span data-ttu-id="6af2e-127">(つまり、バックアップ後にサーバーがアップグレードされた)。</span><span class="sxs-lookup"><span data-stu-id="6af2e-127">That is, the server was upgraded since the backup was performed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6af2e-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6af2e-128">User Action</span></span>  
 <span data-ttu-id="6af2e-129">この状況での復元プロセスはかなり複雑になるため、最後の手段としてのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="6af2e-129">The restore process in this situation is fairly involved, and used only as a last resort.</span></span> <span data-ttu-id="6af2e-130">詳細については、「[SQL Server の別のビルドにデータベースのシステム バックアップを復元することができません。](https://support.microsoft.com/kb/264474)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6af2e-130">For more information, see"[You cannot restore system database backups to a different build of SQL Server](https://support.microsoft.com/kb/264474)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af2e-131">参照</span><span class="sxs-lookup"><span data-stu-id="6af2e-131">See Also</span></span>  
 [<span data-ttu-id="6af2e-132">システム データベースのバックアップと復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6af2e-132">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
  
