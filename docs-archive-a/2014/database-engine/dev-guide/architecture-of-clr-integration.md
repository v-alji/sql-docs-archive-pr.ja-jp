---
title: CLR 統合のアーキテクチャ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], architecture
- architecture [CLR integration]
ms.assetid: 05e4b872-3d21-46de-b4d5-739b5f2a0cf9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bb32e2c7f5eb2079146a2fee64af2e2dbc1d3356
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634004"
---
# <a name="architecture-of-clr-integration"></a><span data-ttu-id="8deab-102">CLR 統合のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8deab-102">Architecture of CLR Integration</span></span>
  <span data-ttu-id="8deab-103">データベース プログラマは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と .NET Framework CLR (共通言語ランタイム) との統合により、Visual C#、Visual Basic .NET、Visual C++ などの言語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8deab-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR) enables database programmers to use languages such as Visual C#, Visual Basic .NET, and Visual C++.</span></span> <span data-ttu-id="8deab-104">プログラマがこれらの言語を使用して記述できるビジネス ロジックには、関数、ストアド プロシージャ、トリガー、データ型、集計などがあります。</span><span class="sxs-lookup"><span data-stu-id="8deab-104">Functions, stored procedures, triggers, data types, and aggregates are among the kinds of business logic that programmers can write with these languages.</span></span>  
  
 <span data-ttu-id="8deab-105">ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部の CLR 統合アーキテクチャについて説明します。また、安全性、拡張性、効率性に優れ、セキュリティで保護されたユーザー コード実行環境が、このアーキテクチャによってどのように提供されるかについても説明します。</span><span class="sxs-lookup"><span data-stu-id="8deab-105">This section describes the architecture of CLR integration inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and how this architecture provides a safe, scalable, secure, and efficient environment to run user code.</span></span>  
  
 <span data-ttu-id="8deab-106">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="8deab-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="8deab-107">CLR ホスト環境</span><span class="sxs-lookup"><span data-stu-id="8deab-107">CLR Hosted Environment</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
 <span data-ttu-id="8deab-108">CLR 統合アーキテクチャの設計目標、メカニズム、および利点について説明します。</span><span class="sxs-lookup"><span data-stu-id="8deab-108">Discusses architectural design goals, mechanisms, and benefits of CLR integration.</span></span>  
  
 [<span data-ttu-id="8deab-109">CLR 統合のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="8deab-109">Performance of CLR Integration</span></span>](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
 <span data-ttu-id="8deab-110">CLR 統合アーキテクチャのパフォーマンスに関する考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="8deab-110">Covers performance considerations of the CLR integration architecture.</span></span>  
  
  
