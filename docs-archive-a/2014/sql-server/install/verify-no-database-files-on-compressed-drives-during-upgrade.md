---
title: アップグレード処理中に、圧縮されたドライブにデータベースファイルがないことを確認する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c04f7890ba8d8efe64afaf11b922af156c5de46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632275"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a><span data-ttu-id="6ed5d-102">アップグレード処理中にデータベース ファイルが圧縮ドライブにないことを確認する</span><span class="sxs-lookup"><span data-stu-id="6ed5d-102">Verify that no database files are on compressed drives during the upgrade process</span></span>
  <span data-ttu-id="6ed5d-103">アップグレード アドバイザーが圧縮ドライブにデータベース ファイルを検出しました。</span><span class="sxs-lookup"><span data-stu-id="6ed5d-103">Upgrade Advisor detected database files on a compressed drive.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6ed5d-104">では、圧縮ドライブにデータベースを作成できません。圧縮ドライブのデータベースをアップグレードすることもできません。</span><span class="sxs-lookup"><span data-stu-id="6ed5d-104">cannot create or upgrade databases on compressed drives.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6ed5d-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6ed5d-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="6ed5d-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="6ed5d-106">Corrective Action</span></span>  
 <span data-ttu-id="6ed5d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールするとき、システム データベースの保存場所として圧縮されていないドライブを選択します。また、アップグレード対象のデータベースが、圧縮ドライブに格納されていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6ed5d-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select an uncompressed drive for system databases and verify that databases to be upgraded are not on compressed drives.</span></span> <span data-ttu-id="6ed5d-108">ただし、データベースをアップグレードした後は、読み取り専用データベースと読み取り専用セカンダリ ファイル グループを NTFS 圧縮ファイル システムに配置できます。</span><span class="sxs-lookup"><span data-stu-id="6ed5d-108">However, note that after the database has been upgraded, you can put read-only databases and read-only secondary filegroups on an NTFS compressed file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed5d-109">参照</span><span class="sxs-lookup"><span data-stu-id="6ed5d-109">See Also</span></span>  
 <span data-ttu-id="6ed5d-110">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="6ed5d-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="6ed5d-111">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="6ed5d-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
