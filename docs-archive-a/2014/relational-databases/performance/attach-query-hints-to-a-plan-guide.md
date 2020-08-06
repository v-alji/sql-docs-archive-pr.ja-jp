---
title: プラン ガイドへのクエリ ヒントのアタッチ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 074c69ffefd2b5a7b2ef445f941f97b7130b0732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642752"
---
# <a name="attach-query-hints-to-a-plan-guide"></a><span data-ttu-id="7ce4b-102">プラン ガイドへのクエリ ヒントのアタッチ</span><span class="sxs-lookup"><span data-stu-id="7ce4b-102">Attach Query Hints to a Plan Guide</span></span>
  <span data-ttu-id="7ce4b-103">クエリ ヒントは、有効なものであれば、任意の組み合わせでプラン ガイドに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-103">Any combination of valid query hints can be used in a plan guide.</span></span> <span data-ttu-id="7ce4b-104">プラン ガイドをクエリと照合する際、コンパイルや最適化が行われる前に、そのプラン ガイドのヒント句で指定されている OPTION 句がクエリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-104">When a plan guide matches a query, the OPTION clause specified in the hints clause of a plan guide is added to the query before it compiles and optimizes.</span></span> <span data-ttu-id="7ce4b-105">プラン ガイドと照合するクエリで既に OPTION 句が使用されている場合、クエリ内のクエリ ヒントがプラン ガイドで指定されているクエリ ヒントに置換されます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-105">If a query that is matched to a plan guide already has an OPTION clause, the query hints specified in the plan guide replace those in the query.</span></span> <span data-ttu-id="7ce4b-106">ただし、既に OPTION 句が使用されているクエリと照合するプラン ガイドでは、sp_create_plan_guide ステートメントで照合するクエリのテキストを指定するときに、そのクエリの OPTION 句を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-106">However, for a plan guide to match a query that already has an OPTION clause, you must include the OPTION clause of the query when you specify the text of the query to match in the sp_create_plan_guide statement.</span></span> <span data-ttu-id="7ce4b-107">プラン ガイドで指定されたヒントを、クエリの既存のヒントに代わりに使用するのではなく、既存のヒントに追加する場合は、既存のヒントと追加するヒントの両方をプラン ガイドの OPTION 句で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-107">If you want the hints specified in the plan guide to be added to the hints that already exist on the query, instead of replacing them, you must specify both the original hints and the additional hints in the OPTION clause of the plan guide.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7ce4b-108">クエリ ヒントの使用方法が正しくないプラン ガイドは、コンパイル、実行、またはパフォーマンスに関する問題の原因になることがあります。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-108">Plan guides that misuse query hints can cause compilation, execution, or performance problems.</span></span> <span data-ttu-id="7ce4b-109">プラン ガイドは、上級開発者とデータベース管理者のみが使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-109">Plan guides should be used only by experienced developers and database administrators.</span></span>  
  
## <a name="common-query-hints-used-in-plan-guides"></a><span data-ttu-id="7ce4b-110">プラン ガイドで使用される一般的なクエリ ヒント</span><span class="sxs-lookup"><span data-stu-id="7ce4b-110">Common Query Hints Used in Plan Guides</span></span>  
 <span data-ttu-id="7ce4b-111">通常、プラン ガイドからメリットを得られる可能性があるクエリは、パラメーター ベースのものです。このようなクエリはキャッシュされたクエリ プランを使用しますが、最悪のシナリオや最も典型的なシナリオにパラメーター値が対応していないために、クエリのパフォーマンスが低くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-111">Queries that can benefit from plan guides are generally parameter-based, and may be performing poorly because they use cached query plans whose parameter values do not represent a worst-case or most representative scenario.</span></span> <span data-ttu-id="7ce4b-112">この問題に対処するのに、OPTIMIZE FOR クエリ ヒントと RECOMPILE クエリ ヒントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-112">The OPTIMIZE FOR and RECOMPILE query hints can be used to address this problem.</span></span> <span data-ttu-id="7ce4b-113">OPTIMIZE FOR は、クエリの最適化時にパラメーターに特定の値を使用するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に指示するクエリ ヒントです。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-113">OPTIMIZE FOR instructs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use a particular value for a parameter when the query is optimized.</span></span> <span data-ttu-id="7ce4b-114">RECOMPILE は、クエリ プランを実行後に破棄し、次に同じクエリが実行されるときに、クエリ オプティマイザーにより新しいクエリ プランに強制的に再コンパイルされるようにサーバーに指示するクエリ ヒントです。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-114">RECOMPILE instructs the server to discard a query plan after execution, forcing the query optimizer to recompile a new query plan the next time that the same query is executed.</span></span> <span data-ttu-id="7ce4b-115">例については、「 [プラン ガイド](plan-guides.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-115">For an example, see [Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="7ce4b-116">また、INDEX、FORCESCAN、および FORCESEEK のテーブル ヒントをクエリ ヒントとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-116">In addition, you can specify the table hints INDEX, FORCESCAN, and FORCESEEK as query hints.</span></span> <span data-ttu-id="7ce4b-117">クエリ ヒントとして指定すると、これらのヒントはインライン テーブルまたはビュー ヒントと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-117">When specified as query hints, these hints behave like an inline table or view hint.</span></span> <span data-ttu-id="7ce4b-118">INDEX ヒントは、指定したインデックスのみを使用して、参照されているテーブルやビューのデータにアクセスするよう、クエリ オプティマイザーに指示します。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-118">The INDEX hint forces the query optimizer to use only the specified indexes to access the data in the referenced table or view.</span></span> <span data-ttu-id="7ce4b-119">FORCESEEK ヒントは、インデックスのシーク操作のみを使用して参照先テーブルやビューのデータにアクセスするよう、オプティマイザーに指示します。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-119">The FORCESEEK hint forces the optimizer to use only an index seek operation to access the data in the referenced table or view.</span></span> <span data-ttu-id="7ce4b-120">これらのヒントによってプラン ガイド機能が拡張され、プラン ガイドを使用するクエリをさらに最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="7ce4b-120">These hints provide additional plan guide functionality and allow you to have more influence over the optimization of queries that use the plan guide.</span></span>  
  
  