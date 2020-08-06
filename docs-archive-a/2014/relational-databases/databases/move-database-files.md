---
title: データベース ファイルの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- files [SQL Server], moving
- data files [SQL Server], moving
- file moving [SQL Server]
- moving full-text catalogs
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- scheduled disk maintenance [SQL Server]
- moving files
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: 89f01b10-5fae-4ed8-b0fb-a4b9f540fd28
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5491f3c4dfd47cac4047d0409c78001be80d6f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736367"
---
# <a name="move-database-files"></a><span data-ttu-id="e1096-102">データベース ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="e1096-102">Move Database Files</span></span>
  <span data-ttu-id="e1096-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントの FILENAME 句で新しいファイルの場所を指定して、システムおよびユーザー データベースを移動することができます。</span><span class="sxs-lookup"><span data-stu-id="e1096-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move system and user databases by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="e1096-104">データ ファイル、ログ ファイル、およびフルテキスト カタログ ファイルもこの方法で移動できます。</span><span class="sxs-lookup"><span data-stu-id="e1096-104">Data, log, and full-text catalog files can be moved in this way.</span></span> <span data-ttu-id="e1096-105">データベース ファイルの移動は、次の状況で便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1096-105">This may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="e1096-106">障害復旧。</span><span class="sxs-lookup"><span data-stu-id="e1096-106">Failure recovery.</span></span> <span data-ttu-id="e1096-107">たとえば、ハードウェア障害により、データベースが問題のあるモードになっている場合や、シャットダウンされた場合など。</span><span class="sxs-lookup"><span data-stu-id="e1096-107">For example, the database is in suspect mode or has shut down, because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="e1096-108">計画に従った再配置。</span><span class="sxs-lookup"><span data-stu-id="e1096-108">Planned relocation.</span></span>  
  
-   <span data-ttu-id="e1096-109">スケジュールされたディスク メンテナンスとしての再配置。</span><span class="sxs-lookup"><span data-stu-id="e1096-109">Relocation for scheduled disk maintenance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1096-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e1096-110">In This Section</span></span>  
  
|<span data-ttu-id="e1096-111">トピック</span><span class="sxs-lookup"><span data-stu-id="e1096-111">Topic</span></span>|<span data-ttu-id="e1096-112">説明</span><span class="sxs-lookup"><span data-stu-id="e1096-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e1096-113">ユーザー データベースの移動</span><span class="sxs-lookup"><span data-stu-id="e1096-113">Move User Databases</span></span>](move-user-databases.md)|<span data-ttu-id="e1096-114">ユーザー データベース ファイルおよびフルテキスト カタログ ファイルを新しい場所に移動する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1096-114">Describes the procedures for moving user database files and full-text catalog files to a new location.</span></span>|  
|[<span data-ttu-id="e1096-115">システム データベースの移動</span><span class="sxs-lookup"><span data-stu-id="e1096-115">Move System Databases</span></span>](system-databases.md)|<span data-ttu-id="e1096-116">システム データベース ファイルを新しい場所に移動する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1096-116">Describes the procedures for moving system database files to a new location.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1096-117">参照</span><span class="sxs-lookup"><span data-stu-id="e1096-117">See Also</span></span>  
 <span data-ttu-id="e1096-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1096-118">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="e1096-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e1096-119">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="e1096-120">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e1096-120">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
