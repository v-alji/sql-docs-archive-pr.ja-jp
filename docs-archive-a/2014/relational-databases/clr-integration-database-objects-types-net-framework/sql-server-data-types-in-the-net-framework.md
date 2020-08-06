---
title: .NET Framework | の SQL Server データ型Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- System.Data library
- System.Data.SqlTypes namespace
- data types [CLR integration]
- SqlTypes library
- database objects [CLR integration], data types
- common language runtime [SQL Server], data types
- building database objects [CLR integration], data types
- mapping data types [CLR integration]
ms.assetid: c70d3ffe-2c32-45a5-849b-ef113dda09b9
author: rothja
ms.author: jroth
ms.openlocfilehash: fe0ed680e7050c58738301256575e4138f21276f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742270"
---
# <a name="sql-server-data-types-in-the-net-framework"></a><span data-ttu-id="d6872-102">.NET Framework での SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="d6872-102">SQL Server Data Types in the .NET Framework</span></span>
  <span data-ttu-id="d6872-103">`SqlTypes` ライブラリは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework の基本クラス ライブラリの一部です。</span><span class="sxs-lookup"><span data-stu-id="d6872-103">The `SqlTypes` library is part of the base class library of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="d6872-104">このライブラリには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータ型と同じセマンティクスと有効桁数を備えたデータ型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6872-104">It is designed to provide data types with the same semantics and precision as those found in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="d6872-105">このトピックでは、.NET Framework プログラマにとっては新しいセマンティクスについて説明し、`System.Data.SqlTypes` ライブラリに含まれる `System.Data` 名前空間に実装されている型を紹介します。</span><span class="sxs-lookup"><span data-stu-id="d6872-105">This topic describes the new semantics to .NET Framework programmers, and introduces the types implemented in the `System.Data.SqlTypes` namespace that is included in the `System.Data` library.</span></span>  
  
 <span data-ttu-id="d6872-106">このセクションのトピックでは、次の内容について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6872-106">This following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="d6872-107">NULL 値の許容と 3 値論理比較</span><span class="sxs-lookup"><span data-stu-id="d6872-107">Nullability and Three-Value Logic Comparisons</span></span>](nullability-and-three-value-logic-comparisons.md)  
 <span data-ttu-id="d6872-108">CLR (共通言語ランタイム) 統合データ型での NULL 値の扱い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6872-108">Discusses how NULL values are handled with common language runtime (CLR) integration data types.</span></span>  
  
 [<span data-ttu-id="d6872-109">照合順序と CLR 統合データ型</span><span class="sxs-lookup"><span data-stu-id="d6872-109">Collation and CLR Integration Data Types</span></span>](collation-and-clr-integration-data-types.md)  
 <span data-ttu-id="d6872-110">CLR 統合での照合順序の扱い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6872-110">Describes how collations are handled with CLR integration.</span></span>  
  
 [<span data-ttu-id="d6872-111">CLR でのラージオブジェクト &#40;LOB&#41; パラメーターの処理</span><span class="sxs-lookup"><span data-stu-id="d6872-111">Handling Large Object &#40;LOB&#41; Parameters in the CLR</span></span>](handling-large-object-lob-parameters-in-the-clr.md)  
 <span data-ttu-id="d6872-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と CLR の間で LOB 型を渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6872-112">Describes how to pass LOB types between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the CLR.</span></span>  
  
 [<span data-ttu-id="d6872-113">CLR パラメーター データのマッピング</span><span class="sxs-lookup"><span data-stu-id="d6872-113">Mapping CLR Parameter Data</span></span>](mapping-clr-parameter-data.md)  
 <span data-ttu-id="d6872-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、CLR 統合、および .NET Framework の間のデータ型マッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d6872-114">Shows data type mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], CLR integration, and the .NET Framework.</span></span>  
  
  
