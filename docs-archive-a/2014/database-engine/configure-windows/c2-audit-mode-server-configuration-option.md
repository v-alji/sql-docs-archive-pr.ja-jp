---
title: c2 audit mode サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- auditing [SQL Server]
- audits [SQL Server], C2 Audit Mode option
- C2 auditing
- C2 Audit Mode option
- recording attempts
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3407a2a94a43adb2d3d3b52994093d6ed0c2e684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740435"
---
# <a name="c2-audit-mode-server-configuration-option"></a><span data-ttu-id="5e208-102">c2 audit mode サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="5e208-102">c2 audit mode Server Configuration Option</span></span>
  <span data-ttu-id="5e208-103">C2 audit mode は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、 **sp_configure** の **c2 audit mode**オプションを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="5e208-103">C2 audit mode can be configured through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or with the **c2 audit mode** option in **sp_configure**.</span></span> <span data-ttu-id="5e208-104">このオプションを選択すると、ステートメントやオブジェクトへの失敗したアクセス試行と成功したアクセス試行の両方が記録されるようにサーバーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="5e208-104">Selecting this option will configure the server to record both failed and successful attempts to access statements and objects.</span></span> <span data-ttu-id="5e208-105">この情報は、システムの利用状況を把握し、発生する可能性のあるセキュリティ ポリシー違反を追跡するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5e208-105">This information can help you profile system activity and track possible security policy violations.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="5e208-106">C2 セキュリティ標準に代わって Common Criteria 認定が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5e208-106">The C2 security standard has been superseded by Common Criteria Certification.</span></span> <span data-ttu-id="5e208-107">「 [common criteria compliance enabled サーバー構成オプション](common-criteria-compliance-enabled-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e208-107">See the [common criteria compliance enabled Server Configuration Option](common-criteria-compliance-enabled-server-configuration-option.md).</span></span>  
  
## <a name="audit-log-file"></a><span data-ttu-id="5e208-108">監査ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="5e208-108">Audit Log File</span></span>  
 <span data-ttu-id="5e208-109">C2 audit mode のデータは、インスタンスの既定のデータ ディレクトリにあるファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="5e208-109">C2 audit mode data is saved in a file in the default data directory of the instance.</span></span> <span data-ttu-id="5e208-110">監査ログ ファイルがファイル サイズの上限である 200 (MB) に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により新しいファイルが作成され、古いファイルが閉じられて、新しい監査レコードはすべて新しいファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5e208-110">If the audit log file reaches its size limit of 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will create a new file, close the old file, and write all new audit records to the new file.</span></span> <span data-ttu-id="5e208-111">この処理は、監査データ ディレクトリがいっぱいになるか、または監査が無効になるまで続行されます。</span><span class="sxs-lookup"><span data-stu-id="5e208-111">This process will continue until the audit data directory fills up or auditing is turned off.</span></span> <span data-ttu-id="5e208-112">C2 トレースの状態を確認するには、sys.traces カタログ ビューに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e208-112">To determine the status of a C2 trace, query the sys.traces catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5e208-113">C2 audit mode は、ログ ファイルに大量のイベント情報を保存しますが、このファイルのサイズはすぐに大きくなってしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e208-113">C2 audit mode saves a large amount of event information to the log file, which can grow quickly.</span></span> <span data-ttu-id="5e208-114">ログ ファイルの保存先データ ディレクトリの領域が不足すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="5e208-114">If the data directory in which logs are being saved runs out of space, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will shut itself down.</span></span> <span data-ttu-id="5e208-115">監査が自動的に開始するように設定されている場合、(監査をバイパスする) **-f** フラグを指定してインスタンスを再起動するか、または監査ログ用に追加のディスク領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e208-115">If auditing is set to start automatically, you must either restart the instance with the **-f** flag (which bypasses auditing), or free up additional disk space for the audit log.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="5e208-116">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="5e208-116">Permissions</span></span>  
 <span data-ttu-id="5e208-117">**sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="5e208-117">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e208-118">例</span><span class="sxs-lookup"><span data-stu-id="5e208-118">Example</span></span>  
 <span data-ttu-id="5e208-119">C2 audit mode を有効にする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5e208-119">The following example turns on C2 audit mode.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e208-120">参照</span><span class="sxs-lookup"><span data-stu-id="5e208-120">See Also</span></span>  
 <span data-ttu-id="5e208-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5e208-121">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="5e208-122">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5e208-122">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="5e208-123">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5e208-123">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
