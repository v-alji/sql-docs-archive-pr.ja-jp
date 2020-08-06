---
title: 拡張ストアドプロシージャ DLL 名を登録するには、完全なパスを使用します。Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5ec4ef3fc2e0f2c4834ffa7479a00562ae15d07f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715942"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a><span data-ttu-id="18604-102">完全なパスを使用して、拡張ストアド プロシージャ DLL の名前を登録する</span><span class="sxs-lookup"><span data-stu-id="18604-102">Use the full path to register extended stored procedure DLL names</span></span>
  <span data-ttu-id="18604-103">DLL 名の完全なパスを使用せずに登録されていた拡張ストアド プロシージャは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18604-103">Extended stored procedures that were previously registered without the full path for the DLL name may not work in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="18604-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="18604-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="18604-105">説明</span><span class="sxs-lookup"><span data-stu-id="18604-105">Description</span></span>  
 <span data-ttu-id="18604-106">DLL 名の完全なパスを使用せずに登録されていた拡張ストアド プロシージャは、アップグレードした後に機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18604-106">Extended stored procedures that were previously registered without the full path for the DLL name may not work after you upgrade.</span></span> <span data-ttu-id="18604-107">アップグレード プロセス中に古い BINN ディレクトリが新しいパスに追加されないためです。</span><span class="sxs-lookup"><span data-stu-id="18604-107">This is because the old BINN directory is not added to the new path during the upgrade process.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="18604-108">によって拡張ストアド プロシージャを見つけることができなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18604-108">may not be able to locate the extended stored procedures.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="18604-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="18604-109">Corrective Action</span></span>  
 <span data-ttu-id="18604-110">アップグレードする前に、登録に完全なパス名を使用していない各拡張ストアド プロシージャに対して、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="18604-110">Before you upgrade, follow these steps for each extended stored procedure that was not registered with a full path name:</span></span>  
  
1.  <span data-ttu-id="18604-111">sp_dropextendedproc を実行して、拡張ストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="18604-111">Run sp_dropextendedproc to remove the extended stored procedure.</span></span>  
  
2.  <span data-ttu-id="18604-112">sp_addextendedproc を実行して、完全なパス名で拡張ストアド プロシージャを登録します。</span><span class="sxs-lookup"><span data-stu-id="18604-112">Run sp_addextendedproc to register the extended stored procedure with the full path name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18604-113">参照</span><span class="sxs-lookup"><span data-stu-id="18604-113">See Also</span></span>  
 <span data-ttu-id="18604-114">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="18604-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="18604-115">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="18604-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
