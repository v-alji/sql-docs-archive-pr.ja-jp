---
title: 資格情報 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: faa2b5be7cf6918b5d5232763a96ed4dbbc89e51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643740"
---
# <a name="credentials-database-engine"></a><span data-ttu-id="d1775-102">資格情報 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="d1775-102">Credentials (Database Engine)</span></span>
  <span data-ttu-id="d1775-103">資格情報は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部のリソースへの接続に必要な認証情報 (資格情報) を含むレコードです。</span><span class="sxs-lookup"><span data-stu-id="d1775-103">A credential is a record that contains the authentication information (credentials) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1775-104">この情報は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1775-104">This information is used internally by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1775-105">通常、資格情報には Windows ユーザー名とパスワードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1775-105">Most credentials contain a Windows user name and password.</span></span>  
  
 <span data-ttu-id="d1775-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証経由で接続しているユーザーは、資格情報に格納された情報によって、サーバー インスタンスの外部のリソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="d1775-106">The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by way of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to access resources outside the server instance.</span></span> <span data-ttu-id="d1775-107">外部リソースが Windows である場合、ユーザーは、資格情報に指定されている Windows ユーザーとして認証されます。</span><span class="sxs-lookup"><span data-stu-id="d1775-107">When the external resource is Windows, the user is authenticated as the Windows user specified in the credential.</span></span> <span data-ttu-id="d1775-108">1 つの資格情報を複数の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインにマッピングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d1775-108">A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="d1775-109">ただし、1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインは 1 つの資格情報にしかマップできません。</span><span class="sxs-lookup"><span data-stu-id="d1775-109">However, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can be mapped to only one credential.</span></span>  
  
 <span data-ttu-id="d1775-110">システム資格情報は、自動的に作成され、特定のエンドポイントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d1775-110">System credentials are created automatically and are associated with specific endpoints.</span></span> <span data-ttu-id="d1775-111">システム資格情報の名前は 2 つのシャープ記号 (##) で始まります。</span><span class="sxs-lookup"><span data-stu-id="d1775-111">Names for system credentials start with two hash signs (##).</span></span>  
  
 <span data-ttu-id="d1775-112">資格情報の詳細については、「[資格](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql)情報カタログビュー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1775-112">For more information about credentials, see the [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) catalog view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d1775-113">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="d1775-113">Related Content</span></span>  
 <span data-ttu-id="d1775-114">[Transact-sql&#41;&#40;](/sql/t-sql/statements/create-credential-transact-sql)資格[情報の作成の](../authentication-access/create-a-credential.md)資格情報の作成</span><span class="sxs-lookup"><span data-stu-id="d1775-114">[Create a Credential](../authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span></span>  
  
 [<span data-ttu-id="d1775-115">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="d1775-115">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
