---
title: CLR 統合のセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d99d32a061d8fe78a8ac3642a503cceb45f3809
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639546"
---
# <a name="clr-integration-security"></a><span data-ttu-id="51f9d-102">CLR 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="51f9d-102">CLR Integration Security</span></span>
  <span data-ttu-id="51f9d-103">[!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)]共通言語ランタイム (clr: common language runtime) のセキュリティモデルでは、ステートメント内で実行されている、 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] またはサーバーで実行されている別の clr オブジェクトの異なる種類の clr オブジェクトと clr 以外のオブジェクトの間のアクセスを管理および保護します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-103">The security model of the [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] statement or another CLR object running in the server.</span></span> <span data-ttu-id="51f9d-104">オブジェクト間の呼び出しをリンクと呼びます。</span><span class="sxs-lookup"><span data-stu-id="51f9d-104">The calls between objects are referred to as links.</span></span> <span data-ttu-id="51f9d-105">このようなオブジェクトに対して実行されるセキュリティ チェックの種類は、関連するリンクの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="51f9d-105">The types of security checks performed on these objects depend on the types of links involved.</span></span>  
  
 <span data-ttu-id="51f9d-106">CLR 統合のセキュリティ モデルは、次のことを目標にしています。</span><span class="sxs-lookup"><span data-stu-id="51f9d-106">The CLR integration security model has the following goals:</span></span>  
  
-   <span data-ttu-id="51f9d-107">既定では、でマネージユーザーコードを実行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-107">By default, running managed user code on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51f9d-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の堅牢性を侵害する可能性のある操作の実行は、レベルの高い適切な権限によって保護されるようにする。</span><span class="sxs-lookup"><span data-stu-id="51f9d-108">Performing operations that potentially compromise the robustness of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should be protected by appropriate high-level permissions.</span></span>  
  
-   <span data-ttu-id="51f9d-109">マネージド ユーザー コードは、データベース内のユーザー データや他のユーザー コードに対して、未承認のアクセスを行わない。</span><span class="sxs-lookup"><span data-stu-id="51f9d-109">Managed user code should not gain unauthorized access to user data or other user code in the database.</span></span> <span data-ttu-id="51f9d-110">ユーザー定義コードは、そのコードを呼び出したユーザー セッションのセキュリティ コンテキストで実行する。実行には、そのセキュリティ コンテキストにおける適切な特権を使用する。</span><span class="sxs-lookup"><span data-stu-id="51f9d-110">User-defined code should run under the security context of the user-session that invoked it, and with the correct privileges for that security context.</span></span>  
  
-   <span data-ttu-id="51f9d-111">ユーザー コードからサーバー外部のリソースへのアクセスを禁止するための制御機能を備える。ユーザー コードの使用は、ローカル データのアクセスおよびコンピューティングに限定する。</span><span class="sxs-lookup"><span data-stu-id="51f9d-111">There should be controls for restricting user code from accessing any resources outside the server, using it strictly for local data access and computation.</span></span>  
  
-   <span data-ttu-id="51f9d-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロセスで実行することによって、ユーザー定義コードがシステム リソースへの未承認のアクセス手段を獲得してはならない。</span><span class="sxs-lookup"><span data-stu-id="51f9d-112">User-defined code should not be able to gain unauthorized access to system resources by virtue of running in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="51f9d-113">CLR のコードアクセスベースのセキュリティモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-113">with the code access-based security model of the CLR.</span></span> <span data-ttu-id="51f9d-114">このセクションでは、このようにセキュリティ モデルを組み合わせたアプローチによるメリットの一部を紹介します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-114">Some of the advantages of this combined approach to security are discussed in this section.</span></span>  
  
 <span data-ttu-id="51f9d-115">次の表に、このセクションの各トピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-115">The following table lists the topics in this section.</span></span>  
  
 [<span data-ttu-id="51f9d-116">CLR 統合のコード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="51f9d-116">CLR Integration Code Access Security</span></span>](clr-integration-code-access-security.md)  
 <span data-ttu-id="51f9d-117">マネージド コードのコード アクセス セキュリティ (CAS) モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-117">Discusses the code access security (CAS) model for managed code.</span></span>  
  
 [<span data-ttu-id="51f9d-118">ホスト保護属性と CLR 統合プログラミング</span><span class="sxs-lookup"><span data-stu-id="51f9d-118">Host Protection Attributes and CLR Integration Programming</span></span>](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 <span data-ttu-id="51f9d-119">SAFE アセンブリと EXTERNAL_ACCESS アセンブリで許可されていないホスト保護属性 (HPA) の値に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-119">Provides information about the host protection attribute (HPA) values that are disallowed in SAFE and EXTERNAL_ACCESS assemblies.</span></span>  
  
 [<span data-ttu-id="51f9d-120">CLR 統合のセキュリティのリンク</span><span class="sxs-lookup"><span data-stu-id="51f9d-120">Links in CLR Integration Security</span></span>](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 <span data-ttu-id="51f9d-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内のユーザー コードが相互に呼び出すしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-121">Describes how pieces of user-code can call each other in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="51f9d-122">権限借用と CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="51f9d-122">Impersonation and CLR Integration Security</span></span>](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 <span data-ttu-id="51f9d-123">権限借用を使用してマネージド コードが外部リソースにアクセスするしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-123">Discusses how managed code accesses external resources using impersonation.</span></span>  
  
 [<span data-ttu-id="51f9d-124">部分的に信頼される呼び出し元の許容</span><span class="sxs-lookup"><span data-stu-id="51f9d-124">Allowing Partially Trusted Callers</span></span>](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 <span data-ttu-id="51f9d-125">マネージド メソッドが別のアセンブリに含まれるクラスのメソッドを起動する際に生じる問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-125">Discusses issues that arise when a managed method invokes a method in a class contained in another assembly.</span></span>  
  
 [<span data-ttu-id="51f9d-126">アプリケーション ドメインと CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="51f9d-126">Application Domains and CLR Integration Security</span></span>](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 <span data-ttu-id="51f9d-127">アセンブリがアプリケーション ドメインに読み込まれるしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="51f9d-127">Describes how assemblies are loaded into application domains.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f9d-128">参照</span><span class="sxs-lookup"><span data-stu-id="51f9d-128">See Also</span></span>  
 [<span data-ttu-id="51f9d-129">CLR 統合アセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="51f9d-129">Managing CLR Integration Assemblies</span></span>](../assemblies/managing-clr-integration-assemblies.md)  
  
  
