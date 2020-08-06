---
title: TRUSTWORTHY データベース プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23391fe48037d4cd7f69aef7df6649949301a0f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713977"
---
# <a name="trustworthy-database-property"></a><span data-ttu-id="1d92a-102">TRUSTWORTHY データベース プロパティ</span><span class="sxs-lookup"><span data-stu-id="1d92a-102">TRUSTWORTHY Database Property</span></span>
  <span data-ttu-id="1d92a-103">TRUSTWORTHY データベース プロパティを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがデータベースとその内容を信頼するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1d92a-103">The TRUSTWORTHY database property is used to indicate whether the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the database and the contents within it.</span></span> <span data-ttu-id="1d92a-104">この設定は既定では OFF ですが、ALTER DATABASE ステートメントを使用して ON に設定できます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-104">By default, this setting is OFF, but can be set to ON by using the ALTER DATABASE statement.</span></span> <span data-ttu-id="1d92a-105">たとえば、「 `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="1d92a-105">For example, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d92a-106">このオプションを設定するには、 **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d92a-106">To set this option, you must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="1d92a-107">このプロパティを使用することで、次のようなオブジェクトの 1 つが含まれているデータベースをアタッチすることによって生じる特定の脅威を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-107">This property can be used to reduce certain threats that can exist as a result of attaching a database that contains one of the following objects:</span></span>  
  
-   <span data-ttu-id="1d92a-108">EXTERNAL_ACCESS 権限または UNSAFE 権限が設定された、悪意のあるアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="1d92a-108">Malicious assemblies with an EXTERNAL_ACCESS or UNSAFE permission setting.</span></span> <span data-ttu-id="1d92a-109">詳細については、「 [CLR 統合のセキュリティ](../clr-integration/security/clr-integration-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d92a-109">For more information, see [CLR Integration Security](../clr-integration/security/clr-integration-security.md).</span></span>  
  
-   <span data-ttu-id="1d92a-110">高い特権を所持するユーザーとして実行するように定義された悪意のあるモジュール。</span><span class="sxs-lookup"><span data-stu-id="1d92a-110">Malicious modules that are defined to execute as high privileged users.</span></span> <span data-ttu-id="1d92a-111">詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d92a-111">For more information, see [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
 <span data-ttu-id="1d92a-112">どちらの状況でもある程度の特権が必要になり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに既にアタッチされているデータベースのコンテキストで使用されるときは、適切なメカニズムによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-112">Both of these situations require a specific degree of privileges and are protected against by appropriate mechanisms when they are used in the context of a database that is already attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1d92a-113">しかし、データベースがオフラインであれば、データベース ファイルへのアクセス権のあるユーザーは、選択した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータベースをアタッチし、悪意のあるコンテンツをデータベースに追加できます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-113">However, if the database is taken offline, a user that has access to the database file can potentially attach it to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of his or her choice and add malicious content to the database.</span></span> <span data-ttu-id="1d92a-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でデータベースがデタッチされ、再アタッチされると、データベース ファイルへのアクセスを制限する特定の権限が、データ ファイルとログ ファイルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-114">When databases are detached and attached in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], certain permissions are set on the data and log files that restrict access to the database files.</span></span>  
  
 <span data-ttu-id="1d92a-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにアタッチされるデータベースはすぐには信頼できないので、データベースが信頼できるものとして明示的に設定されるまでは、データベースはデータベースのスコープを超えてリソースにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1d92a-115">Because a database that is attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be immediately trusted, the database is not allowed to access resources beyond the scope of the database until the database is explicitly marked trustworthy.</span></span> <span data-ttu-id="1d92a-116">また、データベース外のリソースにアクセスするように設計されているモジュール、および EXTERNAL_ACCESS 権限と UNSAFE 権限のいずれかが設定されているアセンブリを正常に実行するには、追加の要件が課せられます。</span><span class="sxs-lookup"><span data-stu-id="1d92a-116">Also, modules that are designed to access resources outside the database, and assemblies with either the EXTERNAL_ACCESS and UNSAFE permission setting, have additional requirements in order to run successfully.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="1d92a-117">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="1d92a-117">Related Content</span></span>  
 [<span data-ttu-id="1d92a-118">SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター</span><span class="sxs-lookup"><span data-stu-id="1d92a-118">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [<span data-ttu-id="1d92a-119">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1d92a-119">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
