---
title: アップグレード処理中にすべてのファイルグループが書き込み可能であることを確認する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filegroups [SQL Server], writeable
- writeable filegroups [SQL Server]
ms.assetid: 2985efc1-4b14-46c3-abbd-a656b159f23c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8146efb876bf97c36c549a2b58d104592df611e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742749"
---
# <a name="verify-all-filegroups-are-writeable-during-the-upgrade-process"></a><span data-ttu-id="174ab-102">アップグレード処理中にすべてのファイル グループが書き込み可能であることを確認する</span><span class="sxs-lookup"><span data-stu-id="174ab-102">Verify all filegroups are writeable during the upgrade process</span></span>
  <span data-ttu-id="174ab-103">アップグレード アドバイザーによって、1 つ以上の読み取り専用のファイル グループを含むデータベースが検出されました。</span><span class="sxs-lookup"><span data-stu-id="174ab-103">Upgrade Advisor detected a database that has one or more read-only filegroups.</span></span> <span data-ttu-id="174ab-104">アップグレードする前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内のすべてのデータベースでファイル グループを READ_WRITE に設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="174ab-104">All databases in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have filegroups set to READ_WRITE before upgrading.</span></span>  
  
## <a name="component"></a><span data-ttu-id="174ab-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="174ab-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="174ab-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="174ab-106">Corrective Action</span></span>  
 <span data-ttu-id="174ab-107">ALTER DATABASE を使用してファイル グループを READ_WRITE に設定してください。</span><span class="sxs-lookup"><span data-stu-id="174ab-107">Use ALTER DATABASE to set the filegroup to READ_WRITE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174ab-108">参照</span><span class="sxs-lookup"><span data-stu-id="174ab-108">See Also</span></span>  
 <span data-ttu-id="174ab-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="174ab-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="174ab-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="174ab-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
