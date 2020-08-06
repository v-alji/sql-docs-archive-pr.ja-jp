---
title: Sysadmin ユーザーのみがファイルシステムにジョブステップのログファイルを書き込むことができます |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- job step log files [SQL Server Agent]
- log files [SQL Server Agent]
- writing job step log files
ms.assetid: d26a7cef-1a60-4c95-b9df-f8b4fec59f9b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e2bf5095ac1e6b67f6c6f3f87444879913916e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641411"
---
# <a name="only-sysadmin-users-can-write-job-step-log-files-to-the-file-system"></a><span data-ttu-id="ebb39-102">sysadmin ユーザーのみがジョブ ステップのログ ファイルをファイル システムに書き込むことができる</span><span class="sxs-lookup"><span data-stu-id="ebb39-102">Only sysadmin users can write job step log files to the file system</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ebb39-103">では、オプションで各ジョブ ステップのログが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="ebb39-103">optionally writes a log for each job step.</span></span>  
  
## <a name="component"></a><span data-ttu-id="ebb39-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ebb39-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ebb39-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="ebb39-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="ebb39-106">説明</span><span class="sxs-lookup"><span data-stu-id="ebb39-106">Description</span></span>  
 <span data-ttu-id="ebb39-107">では [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 、エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin**固定サーバーロールのメンバーが所有するジョブのログをファイルシステムに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ebb39-107">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system for jobs that are owned by members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="ebb39-108">ジョブの所有者が**sysadmin**ロールのメンバーではなく、プロキシアカウントが有効になっている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはプロキシアカウントの資格情報を使用してファイルシステムにログを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ebb39-108">If the job owner is not a member of the **sysadmin** role and if the proxy account is enabled, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can write logs to the file system by using the credentials of the proxy account.</span></span>  
  
 <span data-ttu-id="ebb39-109">アップグレード後に、 **sysadmin**固定サーバーロールのメンバーではないユーザーが所有するジョブは、ログをファイルシステムに書き込むことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="ebb39-109">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** fixed server role can no longer write logs to the file system.</span></span> <span data-ttu-id="ebb39-110">代わりに、これらのユーザーは、 **msdb**データベースのテーブルにログを書き込むオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ebb39-110">Instead, these users can select the option to write their logs to a table in the **msdb** database.</span></span> <span data-ttu-id="ebb39-111">**Sysadmin**ロールのメンバーは、ログファイルをファイルシステムに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ebb39-111">Members of the **sysadmin** role can still write log files to the file system.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="ebb39-112">修正措置</span><span class="sxs-lookup"><span data-stu-id="ebb39-112">Corrective Action</span></span>  
 <span data-ttu-id="ebb39-113">アップグレード後、 **sysadmin**ロールのメンバーではないユーザーが所有するジョブは引き続き実行されますが、ログは作成されません。</span><span class="sxs-lookup"><span data-stu-id="ebb39-113">After you upgrade, jobs that are owned by users who are not members of the **sysadmin** role will continue to run, but logs will not be created.</span></span> <span data-ttu-id="ebb39-114">ジョブステップをテーブルに記録するには、 **sysadmin**ロールのメンバーでないユーザーがジョブを手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb39-114">To log job steps to a table, users who are not members of the **sysadmin** role must manually update their jobs.</span></span>  
  
 <span data-ttu-id="ebb39-115">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「ジョブの作成」、「ジョブ ステップの作成」、および「複数のジョブ ステップの処理」の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebb39-115">For more information, see the topics "Creating Jobs," "Creating Job Steps," and "Handling Multiple Job Steps" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb39-116">参照</span><span class="sxs-lookup"><span data-stu-id="ebb39-116">See Also</span></span>  
 [<span data-ttu-id="ebb39-117">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="ebb39-117">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
