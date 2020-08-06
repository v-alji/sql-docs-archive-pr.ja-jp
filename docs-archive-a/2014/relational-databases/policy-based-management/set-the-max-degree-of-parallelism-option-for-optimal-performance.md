---
title: 最適なパフォーマンスを実現するための max degree of parallelism オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3043a656cbe1ac1ec40f0d0a67b6eac057005af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740849"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a><span data-ttu-id="88b73-102">最適なパフォーマンスを実現するための max degree of parallelism オプションの設定</span><span class="sxs-lookup"><span data-stu-id="88b73-102">Set the Max Degree of Parallelism Option for Optimal Performance</span></span>
  <span data-ttu-id="88b73-103">このルールでは、値の max degree of parallelism (MAXDOP) オプションが 8 より大きいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="88b73-103">This rule determines whether the max degree of parallelism (MAXDOP) option for a value greater than 8.</span></span> <span data-ttu-id="88b73-104">このオプションを大きな値に設定すると、多くの場合、不要なリソース消費やパフォーマンスの低下が発生します。</span><span class="sxs-lookup"><span data-stu-id="88b73-104">Setting this option to a larger value often causes unwanted resource consumption and performance degradation.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="88b73-105">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="88b73-105">Best Practices Recommendations</span></span>  
 <span data-ttu-id="88b73-106">sp_configure を使用して max degree of parallelism オプションを 8 以下に設定してください。</span><span class="sxs-lookup"><span data-stu-id="88b73-106">Set the max degree of parallelism option to 8 or less by using sp_configure.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="88b73-107">詳細情報</span><span class="sxs-lookup"><span data-stu-id="88b73-107">For More Information</span></span>  
 [<span data-ttu-id="88b73-108">サポート技術情報の資料 329204</span><span class="sxs-lookup"><span data-stu-id="88b73-108">Microsoft Knowledge Base article 329204</span></span>](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [<span data-ttu-id="88b73-109">max degree of parallelism サーバー構成オプションの構成</span><span class="sxs-lookup"><span data-stu-id="88b73-109">Configure the max degree of parallelism Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [<span data-ttu-id="88b73-110">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="88b73-110">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
