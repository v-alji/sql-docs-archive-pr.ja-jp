---
title: CLR ユーザー定義集計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641695"
---
# <a name="clr-user-defined-aggregates"></a><span data-ttu-id="330b1-102">CLR ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="330b1-102">CLR User-Defined Aggregates</span></span>
  <span data-ttu-id="330b1-103">集計関数は、値の集まりに対して計算を実行し、1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="330b1-103">Aggregate functions perform a calculation on a set of values and return a single value.</span></span> <span data-ttu-id="330b1-104">従来、で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `SUM` は、 `MAX` 入力スカラー値のセットに対して演算を実行し、そのセットから1つの集計値を生成するやなどの組み込み集計関数のみがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="330b1-104">Traditionally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has supported only built-in aggregate functions, such as `SUM` or `MAX`, that operate on a set of input scalar values and generate a single aggregate value from that set.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="330b1-105">が [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) と統合されたことにより、開発者はマネージド コードでカスタム集計関数を作成し、[!INCLUDE[tsql](../../includes/tsql-md.md)] や他のマネージド コードから作成した関数にアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="330b1-105">integration with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework common language runtime (CLR) now allows developers to create custom aggregate functions in managed code, and to make these functions accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span>  
  
 <span data-ttu-id="330b1-106">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="330b1-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="330b1-107">CLR ユーザー定義集計の要件</span><span class="sxs-lookup"><span data-stu-id="330b1-107">Requirements for CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates-requirements.md)  
 <span data-ttu-id="330b1-108">CLR ユーザー定義集計関数の実装要件の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="330b1-108">Provides an overview of the requirements for implementing CLR user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="330b1-109">CLR ユーザー定義集計関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="330b1-109">Invoking CLR User-Defined Aggregate Functions</span></span>](clr-user-defined-aggregate-invoking-functions.md)  
 <span data-ttu-id="330b1-110">ユーザー定義集計を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="330b1-110">Explains how to invoke user-defined aggregates.</span></span>  
  
  
