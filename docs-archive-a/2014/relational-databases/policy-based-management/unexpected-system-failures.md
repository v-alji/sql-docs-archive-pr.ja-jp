---
title: 予期しないシステム障害 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b791ba0e3f709288a4e2c5b6add4e74e15d56dee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634446"
---
# <a name="unexpected-system-failures"></a><span data-ttu-id="f187f-102">予期しないシステム障害</span><span class="sxs-lookup"><span data-stu-id="f187f-102">Unexpected System Failures</span></span>
  <span data-ttu-id="f187f-103">このルールでは、コンピューターのイベント ログに SYSTEM イベント 6008 がないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f187f-103">This rule checks for SYSTEM Event 6008 in the computer event log.</span></span> <span data-ttu-id="f187f-104">このイベントは、予期しないシステムのシャットダウンを示します。</span><span class="sxs-lookup"><span data-stu-id="f187f-104">This event indicates an unexpected system shutdown.</span></span> <span data-ttu-id="f187f-105">システムが不安定になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをホストするために必要な安定性や整合性が提供できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f187f-105">The system might be unstable and might not provide the stability and integrity that is required to host an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="f187f-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="f187f-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="f187f-107">予期しないサーバーの再起動の原因をすぐに解決するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを別のコンピューターに移動してください。</span><span class="sxs-lookup"><span data-stu-id="f187f-107">Immediately address the cause of the unexpected server restarts, or move the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another computer.</span></span>  
  
  
