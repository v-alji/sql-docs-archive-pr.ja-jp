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
# <a name="recycle-sql-server-agent-error-logs"></a>[SQL Server エージェント エラー ログの再利用]
  このページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラーログをリサイクルできます。 ログを再利用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動しなくても、現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント エラー ログが閉じ、新しいエラー ログが開始します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで保持されるエラー ログは直前の 9 個までであることに注意してください。 既にエラー ログが 9 個に達している場合は、エラー ログを再利用すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは最も古いエラーログを削除します。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント エラー ログ](sql-server-agent-error-log.md)  
  
  
