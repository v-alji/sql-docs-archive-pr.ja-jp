---
title: Resource データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- system objects [SQL Server]
- read-only databases
- mssqlsystemresource.mdf file
- Resource database [SQL Server]
ms.assetid: d592b2b4-bc36-4eb9-9385-8fe4dff0dced
author: stevestein
ms.author: sstein
ms.openlocfilehash: cca2f9e1ff6069a608beb1df1880b37e15f4e869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640057"
---
# <a name="resource-database"></a><span data-ttu-id="fe0a6-102">Resource データベース</span><span class="sxs-lookup"><span data-stu-id="fe0a6-102">Resource Database</span></span>
  <span data-ttu-id="fe0a6-103">Resource データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に搭載されているすべてのシステム オブジェクトを格納する読み取り専用のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-103">The Resource database is a read-only database that contains all the system objects that are included with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fe0a6-104">のシステム オブジェクト (sys.objects など) は、物理的には Resource データベースに保存されていますが、すべてのデータベースの sys スキーマに論理的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-104">system objects, such as sys.objects, are physically persisted in the Resource database, but they logically appear in the sys schema of every database.</span></span> <span data-ttu-id="fe0a6-105">Resource データベースには、ユーザーのデータやユーザーのメタデータは保持されません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-105">The Resource database does not contain user data or user metadata.</span></span>  
  
 <span data-ttu-id="fe0a6-106">Resource データベースが実装されたことで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいバージョンへのアップグレードを簡単かつ迅速に実行できます。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-106">The Resource database makes upgrading to a new version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an easier and faster procedure.</span></span> <span data-ttu-id="fe0a6-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の以前のバージョンでは、アップグレードを行う場合、システム オブジェクトを削除してから再度作成する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-107">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], upgrading required dropping and creating system objects.</span></span> <span data-ttu-id="fe0a6-108">現在は、すべてのシステム オブジェクトが Resource データベース ファイルに格納されるため、Resource データベース ファイルをローカル サーバーにコピーするだけで、アップグレードを完了できます。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-108">Because the Resource database file contains all system objects, an upgrade is now accomplished simply by copying the single Resource database file to the local server.</span></span>  
  
## <a name="physical-properties-of-resource"></a><span data-ttu-id="fe0a6-109">Resource データベースの物理プロパティ</span><span class="sxs-lookup"><span data-stu-id="fe0a6-109">Physical Properties of Resource</span></span>  
 <span data-ttu-id="fe0a6-110">Resource データベースの物理ファイル名は、mssqlsystemresource.mdf および mssqlsystemresource.ldf です。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-110">The physical file names of the Resource database are mssqlsystemresource.mdf and mssqlsystemresource.ldf.</span></span> <span data-ttu-id="fe0a6-111">これらのファイルは \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ に位置しており、移動してはなりません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-111">These files are located in \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\ and should not be moved.</span></span> <span data-ttu-id="fe0a6-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスには、関連する mssqlsystemresource.mdf ファイルが 1 つだけあり、このファイルが共有されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-112">Each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one and only one associated mssqlsystemresource.mdf file, and instances do not share this file.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fe0a6-113">アップグレードとサービス パックにより、新しいリソース データベースが提供されることがあります。これは BINN フォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-113">Upgrades and service packs sometimes provide a new resource database which is installed to the BINN folder.</span></span> <span data-ttu-id="fe0a6-114">リソース データベースの場所の変更はサポートされておらず、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-114">Changing the location of the resource database is not supported or recommended.</span></span>  
  
## <a name="backing-up-and-restoring-the-resource-database"></a><span data-ttu-id="fe0a6-115">Resource データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="fe0a6-115">Backing Up and Restoring the Resource Database</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fe0a6-116">では、Resource データベースをバックアップできません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-116">cannot back up the Resource database.</span></span> <span data-ttu-id="fe0a6-117">ファイル ベースまたはディスク ベースのバックアップは、mssqlsystemresource.mdf ファイルをデータベース ファイルではなくバイナリ (.EXE) ファイルのように実行できますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用してバックアップを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-117">You can perform your own file-based or a disk-based backup by treating the mssqlsystemresource.mdf file as if it were a binary (.EXE) file, rather than a database file, but you cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to restore your backups.</span></span> <span data-ttu-id="fe0a6-118">mssqlsystemresource.mdf のバックアップ コピーの復元は手動でのみ実行できます。また、現在の Resource データベースを古いバージョンや安全でない可能性のあるバージョンで上書きしないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-118">Restoring a backup copy of mssqlsystemresource.mdf can only be done manually, and you must be careful not to overwrite the current Resource database with an out-of-date or potentially insecure version.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fe0a6-119">mssqlsystemresource.mdf のバックアップを復元した後、それ以降のすべての更新を適用し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-119">After restoring a backup of mssqlsystemresource.mdf, you must reapply any subsequent updates.</span></span>  
  
## <a name="accessing-the-resource-database"></a><span data-ttu-id="fe0a6-120">Resource データベースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="fe0a6-120">Accessing the Resource Database</span></span>  
 <span data-ttu-id="fe0a6-121">Resource データベースの変更は、マイクロソフト カスタマー サポート サービス (CSS) のサポート スタッフの指示がある場合にのみ行ってください。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-121">The Resource database should only be modified by or at the direction of a Microsoft Customer Support Services (CSS) specialist.</span></span> <span data-ttu-id="fe0a6-122">Resource データベースの ID は、常に 32767 です。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-122">The ID of the Resource database is always 32767.</span></span> <span data-ttu-id="fe0a6-123">Resource データベースに関する他の重要な値には、バージョン番号とデータベースの最終更新時刻があります。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-123">Other important values associated with the Resource database are the version number and the last time that the database was updated.</span></span>  
  
 <span data-ttu-id="fe0a6-124">Resource **データベースの** **バージョン番号を確認するには、次のステートメントを使用します** 。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-124">**To determine the version number of the** Resource **database, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceVersion');  
GO  
```  
  
 <span data-ttu-id="fe0a6-125">Resource **データベースの** **最終更新時刻を確認するには、次のステートメントを使用します**。</span><span class="sxs-lookup"><span data-stu-id="fe0a6-125">**To determine when the** Resource **database was last updated, use**:</span></span>  
  
```  
SELECT SERVERPROPERTY('ResourceLastUpdateDateTime');  
GO  
```  
  
 <span data-ttu-id="fe0a6-126">**システム オブジェクトの SQL 定義にアクセスするには、次のように OBJECT_DEFINITION 関数を使用します。**</span><span class="sxs-lookup"><span data-stu-id="fe0a6-126">**To access SQL definitions of system objects, use the OBJECT_DEFINITION function:**</span></span>  
  
```  
SELECT OBJECT_DEFINITION(OBJECT_ID('sys.objects'));  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="fe0a6-127">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="fe0a6-127">Related Content</span></span>  
 [<span data-ttu-id="fe0a6-128">システム データベース</span><span class="sxs-lookup"><span data-stu-id="fe0a6-128">System Databases</span></span>](system-databases.md)  
  
 [<span data-ttu-id="fe0a6-129">データベース管理者用の診断接続</span><span class="sxs-lookup"><span data-stu-id="fe0a6-129">Diagnostic Connection for Database Administrators</span></span>](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
 [<span data-ttu-id="fe0a6-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe0a6-130">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
 [<span data-ttu-id="fe0a6-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fe0a6-131">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
 [<span data-ttu-id="fe0a6-132">シングル ユーザー モードでの SQL Server の起動</span><span class="sxs-lookup"><span data-stu-id="fe0a6-132">Start SQL Server in Single-User Mode</span></span>](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
