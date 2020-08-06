---
title: access check cache サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631244"
---
# <a name="access-check-cache-server-configuration-options"></a><span data-ttu-id="c6dde-102">access check cache サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="c6dde-102">access check cache Server Configuration Options</span></span>
<span data-ttu-id="c6dde-103">データベース オブジェクトに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアクセスすると、アクセス チェックが **access check result cache**と呼ばれる内部構造にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c6dde-103">When database objects are accessed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the access check is cached in an internal structure called the **access check result cache**.</span></span> 
  
<span data-ttu-id="c6dde-104">**access check cache bucket count** オプションは、access check result cache に使用されるハッシュ バケットの数を制御します。</span><span class="sxs-lookup"><span data-stu-id="c6dde-104">The **access check cache bucket count** option controls the number of hash buckets that are used for the access check result cache.</span></span> 

<span data-ttu-id="c6dde-105">**access check cache quota** オプションは、access check result cache に格納されるエントリの数を制御します。</span><span class="sxs-lookup"><span data-stu-id="c6dde-105">The **access check cache quota** option controls the number of entries that are stored in the access check result cache.</span></span> <span data-ttu-id="c6dde-106">エントリが最大数に達すると、最も古いエントリが access check result cache から削除されます。</span><span class="sxs-lookup"><span data-stu-id="c6dde-106">When the maximum number of entries is reached, the oldest entries are removed from the access check result cache.</span></span>
  
<span data-ttu-id="c6dde-107">既定値は 0 で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がこれらのオプションを管理していることを示します。</span><span class="sxs-lookup"><span data-stu-id="c6dde-107">The default values of 0 indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is managing these options.</span></span> <span data-ttu-id="c6dde-108">から [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 、既定値は次の内部構成に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c6dde-108">From [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] through [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the default values translate to the following internal configurations:</span></span>
-   <span data-ttu-id="c6dde-109">アクセス確認キャッシュバケット数の場合、値0は x86 アーキテクチャの場合は256バケット、x64 と IA-64 アーキテクチャの場合は2048バケットの既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c6dde-109">For access check cache bucket count, the value 0 sets a default value of 256 buckets for x86 architecture, and 2,048 buckets for x64 and IA-64 architectures.</span></span>
-   <span data-ttu-id="c6dde-110">アクセス確認キャッシュクォータの場合、値0は、x86 アーキテクチャの場合は1024エントリ、x64 と IA-64 アーキテクチャの場合は28192048バケットの既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c6dde-110">For access check cache quota, the value 0 sets a default value of 1,024 entries for x86 architecture, and 28,192,048 buckets for x64 and IA-64 architectures.</span></span>

<span data-ttu-id="c6dde-111">まれに、これらのオプションを変更することによってパフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6dde-111">In rare circumstances, performance can be improved by changing these options.</span></span> <span data-ttu-id="c6dde-112">たとえば、メモリの使用率が高すぎる場合は、access check result cache のサイズを小さくした方がよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="c6dde-112">For example, you may want to reduce the size of the access check result cache if too much memory is used.</span></span> <span data-ttu-id="c6dde-113">または、アクセス許可の再計算時に CPU の使用率が高い場合は、access check result cache のサイズを大きくした方がよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="c6dde-113">Or, you may want to increase the size of the access check result cache if you experience high CPU usage when permissions are recalculated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6dde-114">これらのオプションはマイクロソフト カスタマー サポート サービスから指示があった場合にのみ変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6dde-114">Microsoft recommends only changing these options when directed by Microsoft Customer Support Services.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c6dde-115">参照</span><span class="sxs-lookup"><span data-stu-id="c6dde-115">See Also</span></span>  
 <span data-ttu-id="c6dde-116">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c6dde-116">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="c6dde-117">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c6dde-117">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
