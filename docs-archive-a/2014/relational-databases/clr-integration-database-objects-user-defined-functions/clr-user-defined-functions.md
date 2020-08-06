---
title: CLR ユーザー定義関数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: ba7a4a983ec0cb36ef0fd79df44491f7f23f7648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643412"
---
# <a name="clr-user-defined-functions"></a><span data-ttu-id="f15d6-102">CLR ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="f15d6-102">CLR User-Defined Functions</span></span>
  <span data-ttu-id="f15d6-103">ユーザー定義関数は、パラメーターを受け取り、計算やその他の動作を実行し、結果を返すルーチンです。</span><span class="sxs-lookup"><span data-stu-id="f15d6-103">User-defined functions are routines that can take parameters, perform calculations or other actions, and return a result.</span></span> <span data-ttu-id="f15d6-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] からは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# などの [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework プログラミング言語でユーザー定義関数を記述できます。</span><span class="sxs-lookup"><span data-stu-id="f15d6-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you can write user-defined functions in any [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework programming language, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="f15d6-105">関数には、1 つの値を返すスカラー関数と行セットを返すテーブル値関数の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="f15d6-105">There are two types of functions: scalar, which returns a single value, and table-valued, which returns a set of rows.</span></span>  
  
 <span data-ttu-id="f15d6-106">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f15d6-106">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="f15d6-107">CLR スカラー値関数</span><span class="sxs-lookup"><span data-stu-id="f15d6-107">CLR Scalar-Valued Functions</span></span>](clr-scalar-valued-functions.md)  
 <span data-ttu-id="f15d6-108">実装の要件とスカラー値関数の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="f15d6-108">Covers implementation requirements and examples of scalar-valued functions.</span></span>  
  
 [<span data-ttu-id="f15d6-109">CLR テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="f15d6-109">CLR Table-Valued Functions</span></span>](clr-table-valued-functions.md)  
 <span data-ttu-id="f15d6-110">TVF (テーブル値関数) の実装方法と使用方法を説明し、[!INCLUDE[tsql](../../includes/tsql-md.md)] TVF と CLR (共通言語ランタイム) TVF の相異点についても説明します。</span><span class="sxs-lookup"><span data-stu-id="f15d6-110">Discusses how to implement and use table-valued functions (TVFs), as well as differences between [!INCLUDE[tsql](../../includes/tsql-md.md)] and common language runtime (CLR) TVFs.</span></span>  
  
 [<span data-ttu-id="f15d6-111">CLR ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="f15d6-111">CLR User-Defined Aggregates</span></span>](clr-user-defined-aggregates.md)  
 <span data-ttu-id="f15d6-112">ユーザー定義集計の実装方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f15d6-112">Describes how to implement and use user-defined aggregates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15d6-113">参照</span><span class="sxs-lookup"><span data-stu-id="f15d6-113">See Also</span></span>  
 [<span data-ttu-id="f15d6-114">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="f15d6-114">User-Defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)  
  
  
