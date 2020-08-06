---
title: SQLXML マネージクラス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- .NET Framework [SQLXML], Managed Classes
- SQL Server .NET Data Provider
- Managed Classes [SQLXML], about managed classes
- providers [SQLXML], SQL Server .NET Data Provider
- data providers [SQLXML], SQL Server .NET Data Provider
- Managed Classes [SQLXML]
- XML [SQLXML]
- SQLXML Managed Classes
- providers [SQLXML], SQLXML Managed Classes
- data providers [SQLXML], SQLXML Managed Classes
- SQLXML, Managed Classes
ms.assetid: 73a5faeb-dabf-4895-acb5-a9651b646065
author: rothja
ms.author: jroth
ms.openlocfilehash: bb8d2d4f2d2fc512901e4ad37f0e46cf696b9475
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630865"
---
# <a name="sqlxml-managed-classes"></a><span data-ttu-id="4d221-102">SQLXML マネージド クラス</span><span class="sxs-lookup"><span data-stu-id="4d221-102">SQLXML Managed Classes</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="4d221-103">SQLXML マネージド クラスでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 内で SQLXML 4.0 の機能へのアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="4d221-103">SQLXML Managed Classes exposes the functionality of SQLXML 4.0 inside the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="4d221-104">SQLXML マネージド クラスを使用すると、C# アプリケーションを作成して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスから XML データにアクセスしたり、.NET Framework 環境にデータを取り込んだり、データを処理したり、変更を DiffGram として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信し適用することができます。</span><span class="sxs-lookup"><span data-stu-id="4d221-104">With SQLXML Managed Classes, you can write a C# application to access XML data from an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], bring the data into the .NET Framework environment, process the data, and send the updates back to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a DiffGram to apply the updates.</span></span> <span data-ttu-id="4d221-105">SQL マネージド クラスを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに更新を適用するときには、マッピング スキーマを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d221-105">You must use a mapping schema when applying updates to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using SQLXML Managed Classes.</span></span> <span data-ttu-id="4d221-106">実際のサンプルについては、「 [.Net 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d221-106">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="4d221-107">SQLXML 4.0 で SQLXML マネージド クラスを使用するには、Microsoft Visual Studio をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d221-107">To use the SQLXML Managed Classes with SQLXML 4.0, you must install Microsoft Visual Studio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d221-108">.NET Framework には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET データ プロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4d221-108">The .NET Framework includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .NET Data Provider.</span></span> <span data-ttu-id="4d221-109">このプロバイダーは .NET 環境から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのアクセスに使用できますが、扱えるのは従来の SQL クエリ (FOR XML クエリ以外のリレーショナル データベース クエリ) だけです。</span><span class="sxs-lookup"><span data-stu-id="4d221-109">This provider can be used to access [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the .NET environment; however, it can handle only traditional SQL queries (that is, relational database queries with the exception of FOR XML queries).</span></span> <span data-ttu-id="4d221-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で XML テンプレートやサーバー側の XPath クエリを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="4d221-110">You cannot execute XML templates or the server-side XPath queries in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d221-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4d221-111">In This Section</span></span>  
 [<span data-ttu-id="4d221-112">SQLXML マネージ クラス オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="4d221-112">SQLXML Managed Classes Object Model</span></span>](../../../database-engine/dev-guide/sqlxml-managed-classes-object-model.md)  
 <span data-ttu-id="4d221-113">SQLXML マネージクラスとそのプロパティおよびメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4d221-113">Documents SQLXML Managed Classes and their properties and methods.</span></span>  
  
 [<span data-ttu-id="4d221-114">SQLXML マネージド クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4d221-114">Using the SQLXML Managed Classes</span></span>](sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="4d221-115">SQLXML マネージド クラスの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d221-115">Provides examples of using SQLXML Managed Classes.</span></span>  
  
  
