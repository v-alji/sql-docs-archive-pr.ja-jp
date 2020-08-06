---
title: System.Data.dll | で許可されていない型とメンバーMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
ms.openlocfilehash: cd62f6f0a90bd167f20a33f8de749acc982f39b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634563"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a><span data-ttu-id="b903f-102">System.Data.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="b903f-102">Disallowed Types and Members in System.Data.dll</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b903f-103">共通言語統合 (CLR) プログラミングでは、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` 、 **sharedstate**、 `Synchronization` 、または `UI` の値を持つ列挙体を指定するを持つ型またはメンバーの使用は禁止されています。</span><span class="sxs-lookup"><span data-stu-id="b903f-103">common language integration (CLR) programming disallows the use of a type or member that has a `HostProtectionAttribute` that specifies a `System.Security.Permissions.HostProtectionResource` enumeration with a value of `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **SharedState**, `Synchronization`, or `UI`.</span></span> <span data-ttu-id="b903f-104">次の表は、ホスト保護属性 (HPA) 値が許可されない System.Data.dll アセンブリのメンバーおよび型を示しています。</span><span class="sxs-lookup"><span data-stu-id="b903f-104">The following table lists the members and types of the System.Data.dll assembly whose Host Protection Attribute (HPA) values are disallowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b903f-105">この一覧は、サポートされているアセンブリから作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="b903f-105">This list was generated from the supported assemblies.</span></span> <span data-ttu-id="b903f-106">詳細については、「[サポートされている .NET Framework ライブラリ](../clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b903f-106">For more information, see [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md).</span></span>  
  
|<span data-ttu-id="b903f-107">型またはメンバー</span><span class="sxs-lookup"><span data-stu-id="b903f-107">Type or Member</span></span>|<span data-ttu-id="b903f-108">HPA 値</span><span class="sxs-lookup"><span data-stu-id="b903f-108">HPA Value(s)</span></span>|  
|--------------------|--------------------|  
|<span data-ttu-id="b903f-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span><span class="sxs-lookup"><span data-stu-id="b903f-109">System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()</span></span>|<span data-ttu-id="b903f-110">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-110">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span><span class="sxs-lookup"><span data-stu-id="b903f-111">System.Data.SqlClient.SqlCommand.BeginExecuteReader()</span></span>|<span data-ttu-id="b903f-112">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-112">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span><span class="sxs-lookup"><span data-stu-id="b903f-113">System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()</span></span>|<span data-ttu-id="b903f-114">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-114">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-115">System.Data.SqlClient.SqlDependency..ctor()</span><span class="sxs-lookup"><span data-stu-id="b903f-115">System.Data.SqlClient.SqlDependency..ctor()</span></span>|<span data-ttu-id="b903f-116">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-116">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-117">System.Data.SqlClient.SqlDependency.Start()</span><span class="sxs-lookup"><span data-stu-id="b903f-117">System.Data.SqlClient.SqlDependency.Start()</span></span>|<span data-ttu-id="b903f-118">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-118">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-119">System.Data.SqlClient.SqlDependency.Stop()</span><span class="sxs-lookup"><span data-stu-id="b903f-119">System.Data.SqlClient.SqlDependency.Stop()</span></span>|<span data-ttu-id="b903f-120">ExternalThreading</span><span class="sxs-lookup"><span data-stu-id="b903f-120">ExternalThreading</span></span>|  
|<span data-ttu-id="b903f-121">System.Data.TypedDataSetGenerator</span><span class="sxs-lookup"><span data-stu-id="b903f-121">System.Data.TypedDataSetGenerator</span></span>|<span data-ttu-id="b903f-122">SharedState、Synchronization</span><span class="sxs-lookup"><span data-stu-id="b903f-122">SharedState, Synchronization</span></span>|  
|<span data-ttu-id="b903f-123">System.Xml.XmlDataDocument</span><span class="sxs-lookup"><span data-stu-id="b903f-123">System.Xml.XmlDataDocument</span></span>|<span data-ttu-id="b903f-124">Synchronization</span><span class="sxs-lookup"><span data-stu-id="b903f-124">Synchronization</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b903f-125">参照</span><span class="sxs-lookup"><span data-stu-id="b903f-125">See Also</span></span>  
 <span data-ttu-id="b903f-126">[ホスト保護属性と CLR 統合プログラミング](host-protection-attributes-and-clr-integration-programming.md) </span><span class="sxs-lookup"><span data-stu-id="b903f-126">[Host Protection Attributes and CLR Integration Programming](host-protection-attributes-and-clr-integration-programming.md) </span></span>  
 <span data-ttu-id="b903f-127">[Microsoft.VisualBasic.dllで許可されていない型とメンバー](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span><span class="sxs-lookup"><span data-stu-id="b903f-127">[Disallowed Types and Members in Microsoft.VisualBasic.dll](disallowed-types-and-members-in-microsoft-visualbasic-dll.md) </span></span>  
 <span data-ttu-id="b903f-128">[mscorlib.dllで許可されていない型とメンバー](disallowed-types-and-members-in-mscorlib-dll.md) </span><span class="sxs-lookup"><span data-stu-id="b903f-128">[Disallowed Types and Members in mscorlib.dll](disallowed-types-and-members-in-mscorlib-dll.md) </span></span>  
 <span data-ttu-id="b903f-129">[System.dllで許可されていない型とメンバー](disallowed-types-and-members-in-system-dll.md) </span><span class="sxs-lookup"><span data-stu-id="b903f-129">[Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md) </span></span>  
 [<span data-ttu-id="b903f-130">System.Core.dll の許可されない型およびメンバー</span><span class="sxs-lookup"><span data-stu-id="b903f-130">Disallowed Types and Members in System.Core.dll</span></span>](disallowed-types-and-members-in-system-core-dll.md)  
  
  
