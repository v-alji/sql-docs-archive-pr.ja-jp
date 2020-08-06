---
title: SQL Server の暗号化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743150"
---
# <a name="sql-server-encryption"></a><span data-ttu-id="ea347-102">SQL Server の暗号化</span><span class="sxs-lookup"><span data-stu-id="ea347-102">SQL Server Encryption</span></span>
  <span data-ttu-id="ea347-103">暗号化は、キーまたはパスワードを使用してデータを難読化するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="ea347-103">Encryption is the process of obfuscating data by the use of a key or password.</span></span> <span data-ttu-id="ea347-104">暗号化によって、データは対応する暗号化解除キーまたはパスワードがないと使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ea347-104">This can make the data useless without the corresponding decryption key or password.</span></span> <span data-ttu-id="ea347-105">暗号化では、アクセス コントロールの問題は解決されません。</span><span class="sxs-lookup"><span data-stu-id="ea347-105">Encryption does not solve access control problems.</span></span> <span data-ttu-id="ea347-106">ただし、暗号化を使用すると、アクセス コントロールがバイパスされる場合でもデータ損失のリスクが限定されるので、セキュリティが強化されます。</span><span class="sxs-lookup"><span data-stu-id="ea347-106">However, it enhances security by limiting data loss even if access controls are bypassed.</span></span> <span data-ttu-id="ea347-107">たとえば、データベース ホスト コンピューターの構成が適切でない場合に、機密データをハッカーが入手したとしても、その情報が暗号化されていれば、ハッカーはその情報を使用できません。</span><span class="sxs-lookup"><span data-stu-id="ea347-107">For example, if the database host computer is misconfigured and a hacker obtains sensitive data, that stolen information might be useless if it is encrypted.</span></span>  
  
 <span data-ttu-id="ea347-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、接続、データ、およびストアド プロシージャに対して暗号化を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea347-108">You can use encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for connections, data, and stored procedures.</span></span> <span data-ttu-id="ea347-109">次の表に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]での暗号化の詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="ea347-109">The following table contains more information about encryption in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ea347-110">暗号化は、セキュリティの強化に役立つ便利なツールですが、すべてのデータまたは接続に対して考慮すべきものではありません。</span><span class="sxs-lookup"><span data-stu-id="ea347-110">Although encryption is a valuable tool to help ensure security, it should not be considered for all data or connections.</span></span> <span data-ttu-id="ea347-111">暗号化を実装するかどうかを検討する際は、ユーザーがデータにどのようにアクセスするかを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea347-111">When you are deciding whether to implement encryption, consider how users will access data.</span></span> <span data-ttu-id="ea347-112">ユーザーがパブリック ネットワーク経由でデータにアクセスする場合は、セキュリティを強化するためにデータの暗号化が必要になると考えられます。</span><span class="sxs-lookup"><span data-stu-id="ea347-112">If users access data over a public network, data encryption might be required to increase security.</span></span> <span data-ttu-id="ea347-113">一方、すべてのアクセスにセキュリティで保護されたイントラネット構成が使用される場合には、暗号化は必ずしも必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ea347-113">However, if all access involves a secure intranet configuration, encryption might not be required.</span></span> <span data-ttu-id="ea347-114">暗号化を使用する場合は、それに伴ってパスワード、キー、および証明書のメンテナンス計画が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ea347-114">Any use of encryption should also include a maintenance strategy for passwords, keys, and certificates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea347-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ea347-115">In This Section</span></span>  
 [<span data-ttu-id="ea347-116">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="ea347-116">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
 <span data-ttu-id="ea347-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の暗号化階層について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-117">Information about the encryption hierarchy in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="ea347-118">暗号化アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="ea347-118">Choose an Encryption Algorithm</span></span>](choose-an-encryption-algorithm.md)  
 <span data-ttu-id="ea347-119">効果的な暗号化アルゴリズムを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-119">Information about how to select an effective encrypting algorithm.</span></span>  
  
 [<span data-ttu-id="ea347-120">透過的なデータ暗号化 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-120">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)  
 <span data-ttu-id="ea347-121">データを透過的に暗号化する方法に関する一般情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ea347-121">General information about how to encrypt data transparently.</span></span>  
  
 [<span data-ttu-id="ea347-122">SQL Server とデータベースの暗号化キー &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-122">SQL Server and Database Encryption Keys &#40;Database Engine&#41;</span></span>](sql-server-and-database-encryption-keys-database-engine.md)  
 <span data-ttu-id="ea347-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の暗号化キーでは、公開キー、秘密キー、対称キーを組み合わせて機密データの保護に使用します。</span><span class="sxs-lookup"><span data-stu-id="ea347-123">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], encryption keys include a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="ea347-124">このセクションでは、暗号化キーを実装および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-124">This section explains how to implement and manage encryption keys.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ea347-125">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ea347-125">Related Content</span></span>  
 [<span data-ttu-id="ea347-126">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="ea347-126">Securing SQL Server</span></span>](../securing-sql-server.md)  
 <span data-ttu-id="ea347-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プラットフォームを保護する方法、およびユーザーとセキュリティ保護可能なオブジェクトを操作する方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-127">Overview of how to help secure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] platform, and how to work with users and securable objects.</span></span>  
  
 [<span data-ttu-id="ea347-128">暗号化関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-128">Cryptographic Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 <span data-ttu-id="ea347-129">暗号化機能を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-129">Information about how to implement cryptographic functions.</span></span>  
  
 [<span data-ttu-id="ea347-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-130">ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 <span data-ttu-id="ea347-131">パスワードを使用してデータを暗号化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-131">Information about how to use a password to encrypt data.</span></span>  
  
 [<span data-ttu-id="ea347-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-132">ENCRYPTBYKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbykey-transact-sql)  
 <span data-ttu-id="ea347-133">対称キーを使用してデータを暗号化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-133">Information about how to use a symmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="ea347-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-134">ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 <span data-ttu-id="ea347-135">非対称キーを使用してデータを暗号化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-135">Information about how to use an asymmetric key to encrypt data.</span></span>  
  
 [<span data-ttu-id="ea347-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea347-136">ENCRYPTBYCERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/encryptbycert-transact-sql)  
 <span data-ttu-id="ea347-137">証明書を使用してデータを暗号化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea347-137">Information about how to use a certificate to encrypt data.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ea347-138">外部リソース</span><span class="sxs-lookup"><span data-stu-id="ea347-138">External Resources</span></span>  
 [<span data-ttu-id="ea347-139">2005セキュリティを SQL Server するための10の手順</span><span class="sxs-lookup"><span data-stu-id="ea347-139">10 Steps to SQL Server 2005 Security</span></span>](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 <span data-ttu-id="ea347-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセキュリティに関する最新情報が掲載されています。</span><span class="sxs-lookup"><span data-stu-id="ea347-140">Current information about [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea347-141">参照</span><span class="sxs-lookup"><span data-stu-id="ea347-141">See Also</span></span>  
 <span data-ttu-id="ea347-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ea347-142">[sys.key_encryptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql) </span></span>  
 <span data-ttu-id="ea347-143">[SQL Server とデータベースの暗号化キー &#40;データベース エンジン&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="ea347-143">[SQL Server and Database Encryption Keys &#40;Database Engine&#41;](sql-server-and-database-encryption-keys-database-engine.md) </span></span>  
 [<span data-ttu-id="ea347-144">Reporting Services の暗号化キーのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="ea347-144">Back Up and Restore Reporting Services Encryption Keys</span></span>](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
