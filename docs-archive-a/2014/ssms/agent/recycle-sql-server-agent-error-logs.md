---
title: '[SQL Server エージェント エラー ログの再利用] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b30f0a2ba9a2d861d4a36a86489757cde512fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645323"
---
# <a name="recycle-sql-server-agent-error-logs"></a><span data-ttu-id="0c76b-102">[SQL Server エージェント エラー ログの再利用]</span><span class="sxs-lookup"><span data-stu-id="0c76b-102">Recycle SQL Server Agent Error Logs</span></span>
  <span data-ttu-id="0c76b-103">このページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラーログをリサイクルできます。</span><span class="sxs-lookup"><span data-stu-id="0c76b-103">Use this page to recycle the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Error Logs.</span></span> <span data-ttu-id="0c76b-104">ログを再利用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動しなくても、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログが閉じ、新しいエラー ログが開始します。</span><span class="sxs-lookup"><span data-stu-id="0c76b-104">Recycling the log closes the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log and starts a new error log without restarting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="0c76b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで保持されるエラー ログは直前の 9 個までであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0c76b-105">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent maintains the nine most recent error logs.</span></span> <span data-ttu-id="0c76b-106">既にエラー ログが 9 個に達している場合は、エラー ログを再利用すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは最も古いエラーログを削除します。</span><span class="sxs-lookup"><span data-stu-id="0c76b-106">If there are already nine error logs present, recycling the error log causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to remove the oldest error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c76b-107">参照</span><span class="sxs-lookup"><span data-stu-id="0c76b-107">See Also</span></span>  
 [<span data-ttu-id="0c76b-108">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="0c76b-108">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
