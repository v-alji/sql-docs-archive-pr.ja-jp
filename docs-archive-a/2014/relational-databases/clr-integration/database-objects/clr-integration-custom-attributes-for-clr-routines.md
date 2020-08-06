---
title: CLR ルーチンのカスタム属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: 058bbec7f0f1f63fbd96258a0abe7a6c3d543d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631093"
---
# <a name="custom-attributes-for-clr-routines"></a><span data-ttu-id="21ba9-102">CLR ルーチンのカスタム属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-102">Custom Attributes for CLR Routines</span></span>
  <span data-ttu-id="21ba9-103">ここに示されている属性は、に登録されている共通言語ランタイム (CLR) ルーチン、ユーザー定義型、およびユーザー定義集計に適用でき [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="21ba9-103">The attributes listed can be applied to common language runtime (CLR) routines, user-defined types, and user-defined aggregates that are registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21ba9-104">属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-104">If the attribute is not applied, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assumes the default value.</span></span> <span data-ttu-id="21ba9-105">ここで示す属性は、`Microsoft.SqlServer.Server` 名前空間で定義されています。</span><span class="sxs-lookup"><span data-stu-id="21ba9-105">The attributes listed are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a><span data-ttu-id="21ba9-106">SqlUserDefinedAggregate 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-106">The SqlUserDefinedAggregate Attribute</span></span>  
 <span data-ttu-id="21ba9-107">`SqlUserDefinedAggregate` 属性は、ユーザー定義集計として登録する必要のあるメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-107">The `SqlUserDefinedAggregate` attribute indicates that the method should be registered as a user-defined aggregate.</span></span> <span data-ttu-id="21ba9-108">すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="21ba9-108">Every user-defined aggregate must be annotated with this attribute.</span></span>  
  
 <span data-ttu-id="21ba9-109">詳細については、「 [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-109">For more information, see [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).</span></span>  
  
## <a name="the-sqlfunction-attribute"></a><span data-ttu-id="21ba9-110">SqlFunction 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-110">The SqlFunction Attribute</span></span>  
 <span data-ttu-id="21ba9-111">`SqlFunction` 属性は、関数として登録する必要のあるメソッドを示します。この属性を使用する場合は、適切な関数属性セットを指定します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-111">The `SqlFunction` attribute indicates the method should be registered as a function, with the appropriate function attributes set.</span></span>  
  
 <span data-ttu-id="21ba9-112">詳細については、「 [Sqlfunctionattribute](https://go.microsoft.com/fwlink/?LinkId=128019)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-112">For more information, see [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).</span></span>  
  
## <a name="the-sqlfacet-attribute"></a><span data-ttu-id="21ba9-113">SqlFacet 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-113">The SqlFacet Attribute</span></span>  
 <span data-ttu-id="21ba9-114">`SqlFacet` 属性は、UDT (ユーザー定義型) 式の戻り値の型についての情報を返すために使用します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-114">The `SqlFacet` attribute is used to return information about the return type of a user-defined type (UDT) expression.</span></span>  
  
 <span data-ttu-id="21ba9-115">詳細については、「 [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-115">For more information, see [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).</span></span>  
  
## <a name="the-sqlprocedure-attribute"></a><span data-ttu-id="21ba9-116">SqlProcedure 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-116">The SqlProcedure Attribute</span></span>  
 <span data-ttu-id="21ba9-117">`SqlProcedure` 属性は、ストアド プロシージャとして登録する必要のあるメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-117">The `SqlProcedure` attribute indicates the method should be registered as a stored procedure.</span></span> <span data-ttu-id="21ba9-118">この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。</span><span class="sxs-lookup"><span data-stu-id="21ba9-118">This attribute is used only by Visual Studio to register the specified method as a stored procedure automatically; it is not used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="21ba9-119">詳細については、「 [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-119">For more information, see [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).</span></span>  
  
## <a name="the-sqltrigger-attribute"></a><span data-ttu-id="21ba9-120">SqlTrigger 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-120">The SqlTrigger Attribute</span></span>  
 <span data-ttu-id="21ba9-121">`SqlTrigger` 属性は、トリガーとして登録する必要のあるメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-121">The `SqlTrigger` attribute indicates the method should be registered as a trigger.</span></span>  
  
 <span data-ttu-id="21ba9-122">詳細については、「 [Sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=128022) 」と「 [sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=203898)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-122">For more information, see [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) and [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).</span></span>  
  
## <a name="the-sqluserdefinedtypeattribute"></a><span data-ttu-id="21ba9-123">SqlUserDefinedTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="21ba9-123">The SqlUserDefinedTypeAttribute</span></span>  
 <span data-ttu-id="21ba9-124">SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。</span><span class="sxs-lookup"><span data-stu-id="21ba9-124">You can apply the SqlUserDefinedTypeAttribute to a class definition in the assembly.</span></span> <span data-ttu-id="21ba9-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="21ba9-125">It causes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create a user-defined type that is bound to the class definition which has this custom attribute.</span></span>  
  
 <span data-ttu-id="21ba9-126">詳細については、「 [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-126">For more information, see [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).</span></span>  
  
## <a name="the-sqlmethod-attribute"></a><span data-ttu-id="21ba9-127">SqlMethod 属性</span><span class="sxs-lookup"><span data-stu-id="21ba9-127">The SqlMethod Attribute</span></span>  
 <span data-ttu-id="21ba9-128">`SqlMethod` 属性は、UDT のメソッドまたはプロパティの決定性およびデータ アクセス プロパティを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="21ba9-128">The `SqlMethod` attribute is used to indicate the determinism and data access properties of a method or a property on a UDT.</span></span>  
  
 <span data-ttu-id="21ba9-129">詳細については、「 [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21ba9-129">For more information, see [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ba9-130">参照</span><span class="sxs-lookup"><span data-stu-id="21ba9-130">See Also</span></span>  
 <span data-ttu-id="21ba9-131">[CLR ユーザー定義集計](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span><span class="sxs-lookup"><span data-stu-id="21ba9-131">[CLR User-Defined Aggregates](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span></span>  
 <span data-ttu-id="21ba9-132">[CLR ユーザー定義関数](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="21ba9-132">[CLR User-Defined Functions](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="21ba9-133">[CLR ユーザー定義型](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="21ba9-133">[CLR User-Defined Types](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 <span data-ttu-id="21ba9-134">[CLR ストアドプロシージャ](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="21ba9-134">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="21ba9-135">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="21ba9-135">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
