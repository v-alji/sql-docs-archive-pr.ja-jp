---
title: 暗号化アルゴリズムの選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], algorithms
- encryption [SQL Server], algorithms
- security [SQL Server], encryption
- algorithms [SQL Server encryption]
ms.assetid: 8227028c-a9c9-489d-bd27-fbf8242634ae
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 3b2c5292b4a00a3ad81e53fdbc603bb584130613
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741722"
---
# <a name="choose-an-encryption-algorithm"></a><span data-ttu-id="331fe-102">暗号化アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="331fe-102">Choose an Encryption Algorithm</span></span>
  <span data-ttu-id="331fe-103">暗号化は多層防御の 1 つであり、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに対するセキュリティ対策として利用することができます。</span><span class="sxs-lookup"><span data-stu-id="331fe-103">Encryption is one of several defenses-in-depth that are available to the administrator who wants to secure an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="331fe-104">暗号化アルゴリズムによって定義されるデータ変換は、未承認ユーザーが容易に復元できないものです。</span><span class="sxs-lookup"><span data-stu-id="331fe-104">Encryption algorithms define data transformations that cannot be easily reversed by unauthorized users.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="331fe-105">DES、Triple DES、TRIPLE_DES_3KEY、RC2、RC4、128 ビット RC4、DESX、128 ビット AES、192 ビット AES、256 ビット AES など、複数のアルゴリズムがサポートされ、管理者および開発者が必要に応じて選択できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="331fe-105">allows administrators and developers to choose from among several algorithms, including DES, Triple DES, TRIPLE_DES_3KEY, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span>  
  
 <span data-ttu-id="331fe-106">理想的なアルゴリズムは状況によって異なります。また、個々のアルゴリズムの利点についても、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックでは扱っていません。</span><span class="sxs-lookup"><span data-stu-id="331fe-106">No single algorithm is ideal for all situations, and guidance on the merits of each is beyond the scope of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="331fe-107">ただし、一般論としては、次のような原則があります。</span><span class="sxs-lookup"><span data-stu-id="331fe-107">However, the following general principles apply:</span></span>  
  
-   <span data-ttu-id="331fe-108">通常、強力な暗号化では、弱い暗号化よりも多くの CPU リソースを消費します。</span><span class="sxs-lookup"><span data-stu-id="331fe-108">Strong encryption generally consumes more CPU resources than weak encryption.</span></span>  
  
-   <span data-ttu-id="331fe-109">通常、短いキーより長いキーの方が、強力な暗号化を行えます。</span><span class="sxs-lookup"><span data-stu-id="331fe-109">Long keys generally yield stronger encryption than short keys.</span></span>  
  
-   <span data-ttu-id="331fe-110">非対称暗号化は、同じキー長を使用した対称暗号化よりも弱くなりますが、処理速度は比較的遅くなります。</span><span class="sxs-lookup"><span data-stu-id="331fe-110">Asymmetric encryption is weaker than symmetric encryption using the same key length, but it is relatively slow.</span></span>  
  
-   <span data-ttu-id="331fe-111">長いキーを使用したブロック暗号は、ストリーム暗号よりも強力です。</span><span class="sxs-lookup"><span data-stu-id="331fe-111">Block ciphers with long keys are stronger than stream ciphers.</span></span>  
  
-   <span data-ttu-id="331fe-112">長い複雑なパスワードは、短いパスワードよりも強力です。</span><span class="sxs-lookup"><span data-stu-id="331fe-112">Long, complex passwords are stronger than short passwords.</span></span>  
  
-   <span data-ttu-id="331fe-113">大量のデータを暗号化する場合は、対称キーを使用してデータを暗号化し、非対称キーを使用して対称キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="331fe-113">If you are encrypting lots of data, you should encrypt the data using a symmetric key, and encrypt the symmetric key with an asymmetric key.</span></span>  
  
-   <span data-ttu-id="331fe-114">暗号化されたデータは圧縮できませんが、圧縮されたデータは暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="331fe-114">Encrypted data cannot be compressed, but compressed data can be encrypted.</span></span> <span data-ttu-id="331fe-115">圧縮を使用する場合、データを暗号化する前にデータを圧縮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="331fe-115">If you use compression, you should compress data before encrypting it.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="331fe-116">RC4 アルゴリズムは、旧バージョンとの互換性のためにのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="331fe-116">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="331fe-117">データベース互換性レベルが 90 または 100 の場合、新しい素材は RC4 または RC4_128 を使用してのみ暗号化できます</span><span class="sxs-lookup"><span data-stu-id="331fe-117">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="331fe-118">(非推奨)。AES アルゴリズムのいずれかなど、新しいアルゴリズムを使用してください。</span><span class="sxs-lookup"><span data-stu-id="331fe-118">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="331fe-119">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降では、どの互換性レベルでも、RC4 または RC4_128 を使用して暗号化された素材を暗号化解除できます。</span><span class="sxs-lookup"><span data-stu-id="331fe-119">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] and higher material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
>   
>  <span data-ttu-id="331fe-120">異なるデータ ブロックに対して同じ RC4 または RC4_128 KEY_GUID を繰り返し使用すると、同一の RC4 キーが生成されます。これは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が自動的に salt を提供しないためです。</span><span class="sxs-lookup"><span data-stu-id="331fe-120">Repeated use of the same RC4 or RC4_128 KEY_GUID on different blocks of data will result in the same RC4 key because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not provide a salt automatically.</span></span> <span data-ttu-id="331fe-121">同一の RC4 キーを繰り返し使用することは、暗号強度を著しく低下させる周知の間違いです。</span><span class="sxs-lookup"><span data-stu-id="331fe-121">Using the same RC4 key repeatedly is a well-known error that will result in very weak encryption.</span></span> <span data-ttu-id="331fe-122">そのため、RC4 キーワードおよび RC4_128 キーワードは非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="331fe-122">Therefore, we have deprecated the RC4 and RC4_128 keywords.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="331fe-123">暗号化アルゴリズムおよび暗号化テクノロジの詳細については、MSDN の『.NET Framework 開発者ガイド』で、「 [セキュリティの基本概念](https://go.microsoft.com/fwlink/?LinkId=62082) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="331fe-123">For more information about encryption algorithms and encryption technology, see [Key Security Concepts](https://go.microsoft.com/fwlink/?LinkId=62082) in the .NET Framework Developer's Guide on MSDN.</span></span>  
  
 <span data-ttu-id="331fe-124">**DES アルゴリズムに関する説明:**</span><span class="sxs-lookup"><span data-stu-id="331fe-124">**Clarification regarding DES algorithms:**</span></span>  
  
-   <span data-ttu-id="331fe-125">DESX は不適切な名前でした。</span><span class="sxs-lookup"><span data-stu-id="331fe-125">DESX was incorrectly named.</span></span> <span data-ttu-id="331fe-126">ALGORITHM = DESX を使用して作成された対称キーでは、実際には 192 ビット キーを使用した TRIPLE DES 暗号が使用されます。</span><span class="sxs-lookup"><span data-stu-id="331fe-126">Symmetric keys created with ALGORITHM = DESX actually use the TRIPLE DES cipher with a 192-bit key.</span></span> <span data-ttu-id="331fe-127">DESX アルゴリズムは提供されません。</span><span class="sxs-lookup"><span data-stu-id="331fe-127">The DESX algorithm is not provided.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   <span data-ttu-id="331fe-128">ALGORITHM = TRIPLE_DES_3KEY を使用して作成された対称キーでは、192 ビット キーを使用した TRIPLE DES が使用されます。</span><span class="sxs-lookup"><span data-stu-id="331fe-128">Symmetric keys created with ALGORITHM = TRIPLE_DES_3KEY use TRIPLE DES with a 192-bit key.</span></span>  
  
-   <span data-ttu-id="331fe-129">ALGORITHM = TRIPLE_DES を使用して作成された対称キーでは、128 ビット キーを使用した TRIPLE DES が使用されます。</span><span class="sxs-lookup"><span data-stu-id="331fe-129">Symmetric keys created with ALGORITHM = TRIPLE_DES use TRIPLE DES with a 128-bit key.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="331fe-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="331fe-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="331fe-131">対称キーを使用する暗号化</span><span class="sxs-lookup"><span data-stu-id="331fe-131">Encrypting using a symmetric key.</span></span>|[<span data-ttu-id="331fe-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="331fe-132">CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-symmetric-key-transact-sql)|  
|<span data-ttu-id="331fe-133">非対称キーを使用する暗号化</span><span class="sxs-lookup"><span data-stu-id="331fe-133">Encrypting using an asymmetric key.</span></span>|[<span data-ttu-id="331fe-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="331fe-134">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|  
|<span data-ttu-id="331fe-135">証明書を使用する暗号化</span><span class="sxs-lookup"><span data-stu-id="331fe-135">Encrypting using a certificate.</span></span>|[<span data-ttu-id="331fe-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="331fe-136">CREATE CERTIFICATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-certificate-transact-sql)|  
|<span data-ttu-id="331fe-137">透過的なデータ暗号化を使用するデータベース ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="331fe-137">Encrypting database files using transparent data encryption.</span></span>|[<span data-ttu-id="331fe-138">透過的なデータ暗号化 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="331fe-138">Transparent Data Encryption &#40;TDE&#41;</span></span>](transparent-data-encryption.md)|  
|<span data-ttu-id="331fe-139">テーブルの 1 つの列を暗号化する方法</span><span class="sxs-lookup"><span data-stu-id="331fe-139">How to encrypt one column of a table.</span></span>|[<span data-ttu-id="331fe-140">データの列の暗号化</span><span class="sxs-lookup"><span data-stu-id="331fe-140">Encrypt a Column of Data</span></span>](encrypt-a-column-of-data.md)|  
  
## <a name="see-also"></a><span data-ttu-id="331fe-141">参照</span><span class="sxs-lookup"><span data-stu-id="331fe-141">See Also</span></span>  
 <span data-ttu-id="331fe-142">[SQL Server の暗号化](sql-server-encryption.md) </span><span class="sxs-lookup"><span data-stu-id="331fe-142">[SQL Server Encryption](sql-server-encryption.md) </span></span>  
 [<span data-ttu-id="331fe-143">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="331fe-143">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
