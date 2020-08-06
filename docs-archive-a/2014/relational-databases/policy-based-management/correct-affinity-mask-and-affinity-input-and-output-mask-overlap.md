---
title: Affinity Mask と Affinity の入力出力マスクが重複しています |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 486b4441a20db7630082344fb1f277bba053f3ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743222"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a><span data-ttu-id="d5953-102">Affinity Mask と Affinity の入力出力マスクが重複しています</span><span class="sxs-lookup"><span data-stu-id="d5953-102">Correct Affinity Mask and Affinity Input Output Mask Overlap</span></span>
  <span data-ttu-id="d5953-103">このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに、affinity mask オプションと affinity I/O mask オプションの両方が割り当てられたプロセッサが 1 つ以上あるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d5953-103">This rule checks whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has one or more processors that are assigned to be used with both the affinity mask and the affinity I/O mask options.</span></span> <span data-ttu-id="d5953-104">複数のプロセッサが搭載されたコンピューターでは、affinity mask オプションと affinity I/O mask オプションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用される CPU を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5953-104">On a computer that has more than one processor, the affinity mask and the affinity I/O mask options are used to designate which CPUs are used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5953-105">affinity mask と affinity I/O mask の両方で CPU を有効にすると、プロセッサが過剰に使用されるため、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5953-105">Enabling a CPU with both the affinity mask and the affinity I/O mask can slow performance by forcing the processor to be overused.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="d5953-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="d5953-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="d5953-107">affinity mask オプションと affinity I/O mask オプションのいずれかを指定している場合は、両方を指定する必要がありますが、有効にするのは一度に 1 つの CPU だけにしてください。</span><span class="sxs-lookup"><span data-stu-id="d5953-107">When you specify either the affinity mask or the affinity I/O mask options, you should specify both, but only enable each CPU no more than once.</span></span>  
  
 <span data-ttu-id="d5953-108">affinity mask オプションと affinity I/O mask オプションの両方で同じ CPU を有効にしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d5953-108">Do not enable the same CPU in both the affinity mask option and the affinity I/O mask option.</span></span> <span data-ttu-id="d5953-109">各 CPU に対応するビットは、次のいずれかの状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="d5953-109">The bits that correspond to each CPU should be in one of the following states:</span></span>  
  
-   <span data-ttu-id="d5953-110">affinity mask オプションと affinity I/O mask オプションの両方で 0</span><span class="sxs-lookup"><span data-stu-id="d5953-110">0 in both the affinity mask option and the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="d5953-111">affinity mask オプションでは 0、affinity I/O mask オプションでは 1</span><span class="sxs-lookup"><span data-stu-id="d5953-111">0 in the affinity mask option and 1 in the affinity I/O mask option</span></span>  
  
-   <span data-ttu-id="d5953-112">affinity mask オプションでは 1、affinity I/O mask オプションでは 0</span><span class="sxs-lookup"><span data-stu-id="d5953-112">1 in the affinity mask option and 0 in the affinity I/O mask option</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="d5953-113">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d5953-113">For More Information</span></span>  
 [<span data-ttu-id="d5953-114">affinity mask サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="d5953-114">affinity mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="d5953-115">affinity Input-Output mask サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="d5953-115">affinity Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="d5953-116">affinity64 mask サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="d5953-116">affinity64 mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [<span data-ttu-id="d5953-117">affinity64 Input-Output mask サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="d5953-117">affinity64 Input-Output mask Server Configuration Option</span></span>](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a><span data-ttu-id="d5953-118">参照</span><span class="sxs-lookup"><span data-stu-id="d5953-118">See Also</span></span>  
 [<span data-ttu-id="d5953-119">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="d5953-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
