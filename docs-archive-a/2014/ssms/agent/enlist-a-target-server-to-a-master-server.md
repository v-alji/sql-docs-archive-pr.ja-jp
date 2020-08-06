---
title: マスター サーバーへのターゲット サーバーの参加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 256f1a78d298d89a36412ee5689695f3ab3fde8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631475"
---
# <a name="enlist-a-target-server-to-a-master-server"></a><span data-ttu-id="5e563-102">マスター サーバーへのターゲット サーバーの参加</span><span class="sxs-lookup"><span data-stu-id="5e563-102">Enlist a Target Server to a Master Server</span></span>
  <span data-ttu-id="5e563-103">このトピックでは、マルチサーバー管理構成にターゲット サーバーを参加させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e563-103">This topic describes how to add target servers to a multiserver administration configuration.</span></span> <span data-ttu-id="5e563-104">この手順はマスター サーバーから実行します。</span><span class="sxs-lookup"><span data-stu-id="5e563-104">Run this procedure from the master server.</span></span> <span data-ttu-id="5e563-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクト (SMO) を使用します。</span><span class="sxs-lookup"><span data-stu-id="5e563-105">in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="5e563-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス用に使用される Windows アカウントがマルチサーバー環境に与える影響については、「 [マルチサーバー環境の作成](create-a-multiserver-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e563-106">For information about how the Windows account used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service affects a multiserver environment, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="5e563-107">マスター サーバーとターゲット サーバーの間の接続では、完全な Secure Sockets Layer (SSL) 暗号化と証明書の検証が既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="5e563-107">Full Secure Sockets Layer (SSL) encryption and certificate validation is enabled for connections between master servers and target servers by default.</span></span> <span data-ttu-id="5e563-108">詳しくは、「[ターゲット サーバーでの暗号化オプションの設定](set-encryption-options-on-target-servers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5e563-108">For more information, see [Set Encryption Options on Target Servers](set-encryption-options-on-target-servers.md).</span></span>  
  
 <span data-ttu-id="5e563-109">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5e563-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5e563-110">**ターゲット サーバーを参加させるために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="5e563-110">**To enlist a target server, using:**</span></span>  
  
     [<span data-ttu-id="5e563-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5e563-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5e563-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5e563-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="5e563-113">SMO</span><span class="sxs-lookup"><span data-stu-id="5e563-113">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5e563-114">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="5e563-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="5e563-115">ターゲット サーバーを参加させるには</span><span class="sxs-lookup"><span data-stu-id="5e563-115">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="5e563-116">**オブジェクト エクスプローラー**で、マスター サーバーとして構成するサーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5e563-116">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="5e563-117">**[SQL Server エージェント]** を右クリックし、 **[マルチ サーバーの管理]** をポイントして **[ターゲット サーバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e563-117">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Add Target Servers**.</span></span>  
  
3.  <span data-ttu-id="5e563-118">ターゲット サーバー設定ウィザードを実行し、指示に従って操作します。</span><span class="sxs-lookup"><span data-stu-id="5e563-118">Complete the Target Server Wizard, which guides you through the process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5e563-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="5e563-119">Using Transact-SQL</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="5e563-120">ターゲット サーバーを参加させるには</span><span class="sxs-lookup"><span data-stu-id="5e563-120">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="5e563-121">`sp_msx_enlist` ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="5e563-121">Use the `sp_msx_enlist` stored procedure.</span></span>  <span data-ttu-id="5e563-122">詳細については、「 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e563-122">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="5e563-123">SQL Server 管理オブジェクト (SMO) の使用</span><span class="sxs-lookup"><span data-stu-id="5e563-123">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e563-124">参照</span><span class="sxs-lookup"><span data-stu-id="5e563-124">See Also</span></span>  
 [<span data-ttu-id="5e563-125">エンタープライズ全体の管理の自動化</span><span class="sxs-lookup"><span data-stu-id="5e563-125">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
