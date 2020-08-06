---
title: サポートされている .NET Framework ライブラリ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], .NET Framework libraries
- .NET Framework [CLR Integration]
ms.assetid: 417544ff-c25c-496e-add4-2f278f8a4911
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f92e3eadccc869452cf35534f786724c8e259a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631087"
---
# <a name="supported-net-framework-libraries"></a><span data-ttu-id="e6538-102">サポートされている .NET Framework ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e6538-102">Supported .NET Framework Libraries</span></span>
  <span data-ttu-id="e6538-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にホストされている共通言語ランタイム (CLR) を使用すると、ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計をマネージド コードで作成できます。</span><span class="sxs-lookup"><span data-stu-id="e6538-103">With the common language runtime (CLR) hosted in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="e6538-104">.NET Framework クラス ライブラリに用意されている機能を使用すると、文字列操作、高度な算術演算、ファイル アクセス、暗号化などの機能を提供する組み込みのクラスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e6538-104">With the functionality found in the .NET Framework class libraries, you have access to pre-built classes that provide functionality for string manipulation, advanced math operations, file access, cryptography, and more.</span></span> <span data-ttu-id="e6538-105">これらのクラスは、任意のマネージド ストアド プロシージャ、ユーザー定義型、トリガー、ユーザー定義関数、またはユーザー定義集計からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e6538-105">These classes can be accessed from any managed stored procedure, user-defined type, trigger, user-defined function, or user-defined aggregate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6538-106">グローバルアセンブリキャッシュ (GAC) でサポートされていないアセンブリをサービスまたはアップグレードする場合は、を使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="e6538-106">If you service or upgrade unsupported assemblies in the global assembly cache (GAC), your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e6538-107">アセンブリが CLR 統合内に存在する場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e6538-107">If an assembly exists both in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR integration.</span></span> <span data-ttu-id="e6538-108">GAC で、データベースにも登録されているアセンブリ (サポートされていない .NET Framework アセンブリを含む) を提供またはアップグレードする場合は、`ALTER ASSEMBLY` ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内でもアセンブリのコピーを提供またはアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="e6538-108">If you service or upgrade any assemblies in the GAC that are also registered in the database, including unsupported .NET Framework assemblies, make sure to also service or upgrade the copy of the assembly inside your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases with the `ALTER ASSEMBLY` statement.</span></span> <span data-ttu-id="e6538-109">詳細については、[サポート技術情報の記事 949080](https://support.microsoft.com/kb/949080)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6538-109">For more information, see [Knowledge Base article 949080](https://support.microsoft.com/kb/949080).</span></span>  
  
## <a name="supported-libraries"></a><span data-ttu-id="e6538-110">サポートされているライブラリ</span><span class="sxs-lookup"><span data-stu-id="e6538-110">Supported Libraries</span></span>  
 <span data-ttu-id="e6538-111">以降で [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] は、サポートされる .NET Framework ライブラリの一覧が用意されています。これらのライブラリは、を使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] グローバルアセンブリキャッシュ (GAC) から直接読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e6538-111">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] has a list of supported .NET Framework libraries, which have been tested to ensure that they meet reliability and security standards for interaction with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] loads them directly from the Global Assembly Cache (GAC).</span></span>  
  
 <span data-ttu-id="e6538-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の CLR 統合でサポートされるライブラリおよび名前空間を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6538-112">The libraries/namespaces supported by CLR integration in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="e6538-113">CustomMarshalers</span><span class="sxs-lookup"><span data-stu-id="e6538-113">CustomMarshalers</span></span>  
  
-   <span data-ttu-id="e6538-114">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="e6538-114">Microsoft.VisualBasic</span></span>  
  
-   <span data-ttu-id="e6538-115">Microsoft.VisualC</span><span class="sxs-lookup"><span data-stu-id="e6538-115">Microsoft.VisualC</span></span>  
  
-   <span data-ttu-id="e6538-116">mscorlib</span><span class="sxs-lookup"><span data-stu-id="e6538-116">mscorlib</span></span>  
  
-   <span data-ttu-id="e6538-117">システム</span><span class="sxs-lookup"><span data-stu-id="e6538-117">System</span></span>  
  
-   <span data-ttu-id="e6538-118">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="e6538-118">System.Configuration</span></span>  
  
-   <span data-ttu-id="e6538-119">System.Data</span><span class="sxs-lookup"><span data-stu-id="e6538-119">System.Data</span></span>  
  
-   <span data-ttu-id="e6538-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="e6538-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="e6538-121">System.Data.SqlXml</span><span class="sxs-lookup"><span data-stu-id="e6538-121">System.Data.SqlXml</span></span>  
  
-   <span data-ttu-id="e6538-122">System.Deployment</span><span class="sxs-lookup"><span data-stu-id="e6538-122">System.Deployment</span></span>  
  
-   <span data-ttu-id="e6538-123">System.Security</span><span class="sxs-lookup"><span data-stu-id="e6538-123">System.Security</span></span>  
  
-   <span data-ttu-id="e6538-124">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="e6538-124">System.Transactions</span></span>  
  
-   <span data-ttu-id="e6538-125">System.Web.Services</span><span class="sxs-lookup"><span data-stu-id="e6538-125">System.Web.Services</span></span>  
  
-   <span data-ttu-id="e6538-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="e6538-126">System.Xml</span></span>  
  
-   <span data-ttu-id="e6538-127">System.Core.dll</span><span class="sxs-lookup"><span data-stu-id="e6538-127">System.Core.dll</span></span>  
  
-   <span data-ttu-id="e6538-128">System.Xml.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="e6538-128">System.Xml.Linq.dll</span></span>  
  
## <a name="unsupported-libraries"></a><span data-ttu-id="e6538-129">サポートされていないライブラリ</span><span class="sxs-lookup"><span data-stu-id="e6538-129">Unsupported Libraries</span></span>  
 <span data-ttu-id="e6538-130">サポートされていないライブラリは、マネージド ストアド プロシージャ、トリガー、ユーザー定義関数、ユーザー定義型、およびユーザー定義集計から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e6538-130">Unsupported libraries can still be called from your managed stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates.</span></span> <span data-ttu-id="e6538-131">サポートされていないライブラリをコードで使用するには、`CREATE ASSEMBLY` ステートメントを使用して、これらのライブラリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6538-131">The unsupported library must first be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, using the `CREATE ASSEMBLY` statement, before it can be used in your code.</span></span> <span data-ttu-id="e6538-132">サポートされていないライブラリをサーバーに登録して実行する場合は、そのライブラリのセキュリティと信頼性を確認およびテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6538-132">Any unsupported library that is registered and run on the server should be reviewed and tested for security and reliability.</span></span>  
  
 <span data-ttu-id="e6538-133">たとえば、`System.DirectoryServices` 名前空間はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e6538-133">For example, the `System.DirectoryServices` namespace is not supported.</span></span> <span data-ttu-id="e6538-134">System.DirectoryServices.dll アセンブリをコードから呼び出す前に、このアセンブリを `UNSAFE` 権限で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6538-134">You must register the System.DirectoryServices.dll assembly with `UNSAFE` permissions before you can call it from your code.</span></span> <span data-ttu-id="e6538-135">`UNSAFE` 名前空間内のクラスは `System.DirectoryServices` または `SAFE` の要件を満たさないため、`EXTERNAL_ACCESS` 権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e6538-135">The `UNSAFE` permission is necessary because classes in the `System.DirectoryServices` namespace do not meet the requirements for `SAFE` or `EXTERNAL_ACCESS`.</span></span> <span data-ttu-id="e6538-136">詳細については、「 [Clr 統合プログラミングモデルの制限事項](clr-integration-programming-model-restrictions.md)」と「 [Clr 統合コードアクセスセキュリティ](../security/clr-integration-code-access-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6538-136">For more information, see [CLR Integration Programming Model Restrictions](clr-integration-programming-model-restrictions.md) and [CLR Integration Code Access Security](../security/clr-integration-code-access-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6538-137">参照</span><span class="sxs-lookup"><span data-stu-id="e6538-137">See Also</span></span>  
 <span data-ttu-id="e6538-138">[アセンブリの作成](../assemblies/creating-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="e6538-138">[Creating an Assembly](../assemblies/creating-an-assembly.md) </span></span>  
 <span data-ttu-id="e6538-139">[CLR 統合のコードアクセスセキュリティ](../security/clr-integration-code-access-security.md) </span><span class="sxs-lookup"><span data-stu-id="e6538-139">[CLR Integration Code Access Security](../security/clr-integration-code-access-security.md) </span></span>  
 [<span data-ttu-id="e6538-140">CLR 統合プログラミング モデルの制限事項</span><span class="sxs-lookup"><span data-stu-id="e6538-140">CLR Integration Programming Model Restrictions</span></span>](clr-integration-programming-model-restrictions.md)  
  
  
