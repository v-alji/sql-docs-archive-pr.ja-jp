---
title: 暗号化階層 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], hierarchies
- cryptography [SQL Server], hierarchies
- encryption keys [SQL Server]
- security [SQL Server], encryption
- hierarchies [SQL Server], encryption
ms.assetid: 96c276d5-1bba-4e95-b678-10f059f1fbcf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: d38bb83c2f6a2487e547c4686be5c65bc012e33e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741693"
---
# <a name="encryption-hierarchy"></a><span data-ttu-id="6cc65-102">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="6cc65-102">Encryption Hierarchy</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6cc65-103">では、暗号化とキーの階層的な管理インフラストラクチャを使用してデータを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-103">encrypts data with a hierarchical encryption and key management infrastructure.</span></span> <span data-ttu-id="6cc65-104">各層では、証明書、非対称キー、および対称キーの組み合わせを使用して、その層の下位にある層を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-104">Each layer encrypts the layer below it by using a combination of certificates, asymmetric keys, and symmetric keys.</span></span> <span data-ttu-id="6cc65-105">拡張キー管理 (EKM) モジュールで、非対称キーと対称キーを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の外部に格納できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-105">Asymmetric keys and symmetric keys can be stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an Extensible Key Management (EKM) module.</span></span>  
  
 <span data-ttu-id="6cc65-106">次の図は、暗号化階層のそれぞれの層がその下位にある層を暗号化することを示しており、最も一般的な暗号化構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-106">The following illustration shows that each layer of the encryption hierarchy encrypts the layer beneath it, and displays the most common encryption configurations.</span></span> <span data-ttu-id="6cc65-107">階層の先頭へのアクセスは、通常、パスワードで保護されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-107">The access to the start of the hierarchy is usually protected by a password.</span></span>  
  
 <span data-ttu-id="6cc65-108">![いくつかの暗号化の組み合わせをスタック内に表示します。](../../../database-engine/media/encryption-hierarchy-stack.gif "いくつかの暗号化の組み合わせをスタック内に表示します。")</span><span class="sxs-lookup"><span data-stu-id="6cc65-108">![Displays some encryption combinations in a stack.](../../../database-engine/media/encryption-hierarchy-stack.gif "Displays some encryption combinations in a stack.")</span></span>  
  
 <span data-ttu-id="6cc65-109">次の概念に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6cc65-109">Keep in mind the following concepts:</span></span>  
  
-   <span data-ttu-id="6cc65-110">最適なパフォーマンスを得るには、証明書や非対称キーではなく、対称キーを使用してデータを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-110">For best performance, encrypt data using symmetric keys instead of certificates or asymmetric keys.</span></span>  
  
-   <span data-ttu-id="6cc65-111">データベース マスター キーは、サービス マスター キーによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-111">Database master keys are protected by the Service Master Key.</span></span> <span data-ttu-id="6cc65-112">サービス マスター キーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップで作成され、Windows データ保護 API (DPAPI) を使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-112">The Service Master Key is created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] setup and is encrypted with the Windows Data Protection API (DPAPI).</span></span>  
  
-   <span data-ttu-id="6cc65-113">追加の層を重ねる他の暗号化階層も使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-113">Other encryption hierarchies stacking additional layers are possible.</span></span>  
  
-   <span data-ttu-id="6cc65-114">拡張キー管理 (EKM) モジュールは、SQL Server の外部で対称または非対称キーを保持します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-114">An Extensible Key Management (EKM) module holds symmetric or asymmetric keys outside of SQL Server.</span></span>  
  
-   <span data-ttu-id="6cc65-115">透過的なデータ暗号化 (TDE) では、データベース暗号化キーという対称キーを使用する必要があります。データベース暗号化キーは、master データベースのデータベース マスター キーによって保護される証明書、または EKM に格納された非対称キーによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-115">Transparent Data Encryption (TDE) must use a symmetric key called the database encryption key which is protected by either a certificate protected by the database master key of the master database, or by an asymmetric key stored in an EKM.</span></span>  
  
-   <span data-ttu-id="6cc65-116">サービス マスター キーとすべてのデータベース マスター キーは対称キーです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-116">The Service Master Key and all Database Master Keys are symmetric keys.</span></span>  
  
 <span data-ttu-id="6cc65-117">次の図は、同じ情報を別の方法で示しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-117">The following illustration shows the same information in an alternative manner.</span></span>  
  
 <span data-ttu-id="6cc65-118">![いくつかの暗号化の組み合わせをホイール内に表示します。](../../../database-engine/media/encryption-hierarchy-wheel.gif "いくつかの暗号化の組み合わせをホイール内に表示します。")</span><span class="sxs-lookup"><span data-stu-id="6cc65-118">![Displays some encryption combinations in a wheel.](../../../database-engine/media/encryption-hierarchy-wheel.gif "Displays some encryption combinations in a wheel.")</span></span>  
  
 <span data-ttu-id="6cc65-119">この図は、さらに次の概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-119">This diagram illustrates the following additional concepts:</span></span>  
  
-   <span data-ttu-id="6cc65-120">この図では、矢印は一般的な暗号化階層を示しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-120">In this illustration, arrows indicate common encryption hierarchies.</span></span>  
  
-   <span data-ttu-id="6cc65-121">EKM 内の対称キーと非対称キーによって、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に格納されている対称キーと非対称キーへのアクセスを保護できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-121">Symmetric and asymmetric keys in the EKM can protect access to the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6cc65-122">EKM に結ばれた点線は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に格納されている対称キーと非対称キーの代わりに EKM 内のキーを使用できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-122">The dotted line associated with EKM indicates that keys in the EKM could replace the symmetric and asymmetric keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="encryption-mechanisms"></a><span data-ttu-id="6cc65-123">暗号化メカニズム</span><span class="sxs-lookup"><span data-stu-id="6cc65-123">Encryption Mechanisms</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6cc65-124">には、次の暗号化メカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-124">provides the following mechanisms for encryption:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="6cc65-125">関数</span><span class="sxs-lookup"><span data-stu-id="6cc65-125">functions</span></span>  
  
-   <span data-ttu-id="6cc65-126">非対称キー</span><span class="sxs-lookup"><span data-stu-id="6cc65-126">Asymmetric keys</span></span>  
  
-   <span data-ttu-id="6cc65-127">対称キー</span><span class="sxs-lookup"><span data-stu-id="6cc65-127">Symmetric keys</span></span>  
  
-   <span data-ttu-id="6cc65-128">証明書</span><span class="sxs-lookup"><span data-stu-id="6cc65-128">Certificates</span></span>  
  
-   <span data-ttu-id="6cc65-129">透過的なデータ暗号化</span><span class="sxs-lookup"><span data-stu-id="6cc65-129">Transparent Data Encryption</span></span>  
  
### <a name="transact-sql-functions"></a><span data-ttu-id="6cc65-130">Transact-SQL 関数</span><span class="sxs-lookup"><span data-stu-id="6cc65-130">Transact-SQL Functions</span></span>  
 <span data-ttu-id="6cc65-131">個々のアイテムは、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 関数を使用して挿入または更新するときに暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-131">Individual items can be encrypted as they are inserted or updated using [!INCLUDE[tsql](../../../includes/tsql-md.md)] functions.</span></span> <span data-ttu-id="6cc65-132">詳細については、「[ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql)」および「[DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cc65-132">For more information, see [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql) and [DECRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/decryptbypassphrase-transact-sql).</span></span>  
  
### <a name="certificates"></a><span data-ttu-id="6cc65-133">証明書</span><span class="sxs-lookup"><span data-stu-id="6cc65-133">Certificates</span></span>  
 <span data-ttu-id="6cc65-134">通常は単に証明書と呼ばれる公開キー証明書は、公開キーの値を、対応する秘密キーを保持する人物、デバイス、またはサービスの ID にバインドする、デジタル署名されたステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-134">A public key certificate, usually just called a certificate, is a digitally-signed statement that binds the value of a public key to the identity of the person, device, or service that holds the corresponding private key.</span></span> <span data-ttu-id="6cc65-135">証明書は、CA (証明機関) によって発行および書名されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-135">Certificates are issued and signed by a certification authority (CA).</span></span> <span data-ttu-id="6cc65-136">CA から証明書を受け取るエンティティは、その証明書のサブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-136">The entity that receives a certificate from a CA is the subject of that certificate.</span></span> <span data-ttu-id="6cc65-137">通常、証明書には次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-137">Typically, certificates contain the following information.</span></span>  
  
-   <span data-ttu-id="6cc65-138">サブジェクトの公開キー。</span><span class="sxs-lookup"><span data-stu-id="6cc65-138">The public key of the subject.</span></span>  
  
-   <span data-ttu-id="6cc65-139">サブジェクトの ID 情報 (名前や電子メール アドレスなど)。</span><span class="sxs-lookup"><span data-stu-id="6cc65-139">The identifier information of the subject, such as the name and e-mail address.</span></span>  
  
-   <span data-ttu-id="6cc65-140">有効期間。</span><span class="sxs-lookup"><span data-stu-id="6cc65-140">The validity period.</span></span> <span data-ttu-id="6cc65-141">これは、証明書が有効であると見なされる期間です。</span><span class="sxs-lookup"><span data-stu-id="6cc65-141">This is the length of time that the certificate is considered valid.</span></span>  
  
     <span data-ttu-id="6cc65-142">証明書は、証明書で指定された期間中のみ有効です。すべての証明書には、 **有効期間の開始日** と **有効期間の終了日** の日付が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-142">A certificate is valid only for the period of time specified within it; every certificate contains **Valid From** and **Valid To** dates.</span></span> <span data-ttu-id="6cc65-143">これらの日付によって、有効期間の境界が設定されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-143">These dates set the boundaries of the validity period.</span></span> <span data-ttu-id="6cc65-144">証明書の有効期間が終了すると、現在期限が切れている証明書のサブジェクトを使用して新しい証明書を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6cc65-144">When the validity period for a certificate has passed, a new certificate must be requested by the subject of the now-expired certificate.</span></span>  
  
-   <span data-ttu-id="6cc65-145">発行者の ID 情報。</span><span class="sxs-lookup"><span data-stu-id="6cc65-145">Issuer identifier information.</span></span>  
  
-   <span data-ttu-id="6cc65-146">発行者のデジタル署名。</span><span class="sxs-lookup"><span data-stu-id="6cc65-146">The digital signature of the issuer.</span></span>  
  
     <span data-ttu-id="6cc65-147">この署名により、公開キーとサブジェクトの ID 情報のバインドが有効であることが証明されます</span><span class="sxs-lookup"><span data-stu-id="6cc65-147">This signature attests to the validity of the binding between the public key and the identifier information of the subject.</span></span> <span data-ttu-id="6cc65-148">(デジタル署名情報の処理により、その情報だけでなく、送信者が保持している一部の機密情報が署名と呼ばれるタグに変換されます)。</span><span class="sxs-lookup"><span data-stu-id="6cc65-148">(The process of digitally signing information entails transforming the information, as well as some secret information held by the sender, into a tag called a signature.)</span></span>  
  
 <span data-ttu-id="6cc65-149">証明書の主な利点は、個々のサブジェクトのパスワードの設定をホストで保守する必要性がなくなる点です。</span><span class="sxs-lookup"><span data-stu-id="6cc65-149">A primary benefit of certificates is that they relieve hosts of the need to maintain a set of passwords for individual subjects.</span></span> <span data-ttu-id="6cc65-150">ホストでは、証明書の発行者の信頼を確立するだけで済みます。信頼された発行者は、多数の証明書に署名できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-150">Instead, the host merely establishes trust in a certificate issuer, which may then sign an unlimited number of certificates.</span></span>  
  
 <span data-ttu-id="6cc65-151">セキュリティで保護された Web サーバーなどのホストが、信頼されているルート機関として発行者を指定すると、このときホストは、発行された証明書のバインドを確立するために発行者が使用したポリシーを暗黙的に信頼することになります。</span><span class="sxs-lookup"><span data-stu-id="6cc65-151">When a host, such as a secure Web server, designates an issuer as a trusted root authority, the host implicitly trusts the policies that the issuer has used to establish the bindings of certificates it issues.</span></span> <span data-ttu-id="6cc65-152">つまりホストは、証明書のサブジェクトの ID が発行者側で確認されているものと見なします。</span><span class="sxs-lookup"><span data-stu-id="6cc65-152">In effect, the host trusts that the issuer has verified the identity of the certificate subject.</span></span> <span data-ttu-id="6cc65-153">ホストが発行者を信頼されているルート機関として指定する際は、発行者の公開キーが含まれている発行者の自己署名付きの証明書を、ホスト コンピューターの信頼されているルート証明機関の証明書ストアに配置します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-153">A host designates an issuer as a trusted root authority by putting the self-signed certificate of the issuer, which contains the public key of the issuer, into the trusted root certification authority certificate store of the host computer.</span></span> <span data-ttu-id="6cc65-154">中間または下位の証明機関が信頼されるのは、信頼されているルート証明機関からの有効な証明書パスを持っている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-154">Intermediate or subordinate certification authorities are trusted only if they have a valid certification path from a trusted root certification authority.</span></span>  
  
 <span data-ttu-id="6cc65-155">発行者は、証明書の有効期限が切れる前に、証明書を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-155">The issuer can revoke a certificate before it expires.</span></span> <span data-ttu-id="6cc65-156">証明書を取り消すと、証明書で評価されている公開キーと ID のバインドが取り消されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-156">Revocation cancels the binding of a public key to an identity that is asserted in the certificate.</span></span> <span data-ttu-id="6cc65-157">各発行者は、特定の証明書の有効性をチェックするときにプログラムで使用できる、証明書の廃止リストを保持しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-157">Each issuer maintains a certificate revocation list that can be used by programs when they are checking the validity of any given certificate.</span></span>  
  
 <span data-ttu-id="6cc65-158">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって作成された自己署名付きの証明書は、X.509 標準に従っており、X.509 v1 フィールドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-158">The self-signed certificates created by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follow the X.509 standard and support the X.509 v1 fields.</span></span>  
  
### <a name="asymmetric-keys"></a><span data-ttu-id="6cc65-159">非対称キー</span><span class="sxs-lookup"><span data-stu-id="6cc65-159">Asymmetric Keys</span></span>  
 <span data-ttu-id="6cc65-160">非対称キーは、秘密キーとそれに対応する公開キーで構成されています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-160">An asymmetric key is made up of a private key and the corresponding public key.</span></span> <span data-ttu-id="6cc65-161">各キーは、他方のキーで暗号化されたデータを暗号化解除できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-161">Each key can decrypt data encrypted by the other.</span></span> <span data-ttu-id="6cc65-162">非対称の暗号化と暗号化解除は、比較的リソースを集中して消費しますが、対称の暗号化よりも高レベルのセキュリティを提供します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-162">Asymmetric encryption and decryption are relatively resource-intensive, but they provide a higher level of security than symmetric encryption.</span></span> <span data-ttu-id="6cc65-163">非対称キーは、データベース内のストレージに対する対称キーの暗号化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-163">An asymmetric key can be used to encrypt a symmetric key for storage in a database.</span></span>  
  
### <a name="symmetric-keys"></a><span data-ttu-id="6cc65-164">対称キー</span><span class="sxs-lookup"><span data-stu-id="6cc65-164">Symmetric Keys</span></span>  
 <span data-ttu-id="6cc65-165">対称キーは、暗号化と暗号化解除の両方で使用される 1 つのキーです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-165">A symmetric key is one key that is used for both encryption and decryption.</span></span> <span data-ttu-id="6cc65-166">対称キーを使用した暗号化および暗号化解除は、高速であり、データベース内の機密データでの定型的な使用に適しています。</span><span class="sxs-lookup"><span data-stu-id="6cc65-166">Encryption and decryption by using a symmetric key is fast, and suitable for routine use with sensitive data in the database.</span></span>  
  
### <a name="transparent-data-encryption"></a><span data-ttu-id="6cc65-167">透過的なデータ暗号化</span><span class="sxs-lookup"><span data-stu-id="6cc65-167">Transparent Data Encryption</span></span>  
 <span data-ttu-id="6cc65-168">透過的なデータ暗号化 (TDE) は、対称キーを使用した暗号化の特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="6cc65-168">Transparent Data Encryption (TDE) is a special case of encryption using a symmetric key.</span></span> <span data-ttu-id="6cc65-169">TDE では、データベース暗号化キーという対称キーを使用してデータベース全体を暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6cc65-169">TDE encrypts an entire database using that symmetric key called the database encryption key.</span></span> <span data-ttu-id="6cc65-170">データベース暗号化キーは、データベース マスター キーまたは EKM モジュールに格納された非対称キーによって保護される、他のキーまたは証明書によって保護されます。</span><span class="sxs-lookup"><span data-stu-id="6cc65-170">The database encryption key is protected by other keys or certificates which are protected either by the database master key or by an asymmetric key stored in an EKM module.</span></span> <span data-ttu-id="6cc65-171">詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](transparent-data-encryption.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cc65-171">For more information, see [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="6cc65-172">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6cc65-172">Related Content</span></span>  
 [<span data-ttu-id="6cc65-173">SQL Server の保護</span><span class="sxs-lookup"><span data-stu-id="6cc65-173">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
 [<span data-ttu-id="6cc65-174">セキュリティ関数 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6cc65-174">Security Functions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/security-functions-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="6cc65-175">参照</span><span class="sxs-lookup"><span data-stu-id="6cc65-175">See Also</span></span>  
 <span data-ttu-id="6cc65-176">[権限の階層 &#40;データベース エンジン&#41;](../permissions-hierarchy-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="6cc65-176">[Permissions Hierarchy &#40;Database Engine&#41;](../permissions-hierarchy-database-engine.md) </span></span>  
 [<span data-ttu-id="6cc65-177">セキュリティ保護可能</span><span class="sxs-lookup"><span data-stu-id="6cc65-177">Securables</span></span>](../securables.md)  
  
  
