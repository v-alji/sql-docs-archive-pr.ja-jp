---
title: サービス マスター キー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: baeeffd49ac89ce85cf64932fbfd4982d7243887
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743161"
---
# <a name="service-master-key"></a><span data-ttu-id="541a4-102">インスタンスに対して生成される</span><span class="sxs-lookup"><span data-stu-id="541a4-102">Service Master Key</span></span>
  <span data-ttu-id="541a4-103">サービス マスター キーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 暗号化階層のルートです。</span><span class="sxs-lookup"><span data-stu-id="541a4-103">The Service Master Key is the root of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption hierarchy.</span></span> <span data-ttu-id="541a4-104">これは、最初に別のキーを暗号化する必要性が生じたときに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="541a4-104">It is generated automatically the first time it is needed to encrypt another key.</span></span> <span data-ttu-id="541a4-105">既定では、サービス マスター キーはローカル コンピューターのキーを使用し、Windows データ保護 API により暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="541a4-105">By default, the Service Master Key is encrypted using the Windows data protection API and using the local machine key.</span></span> <span data-ttu-id="541a4-106">サービス マスター キーを作成した Windows サービス アカウント、またはサービス アカウント名とサービス アカウントのパスワードの両方にアクセスできるプリンシパルだけが、サービス マスター キーを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="541a4-106">The Service Master Key can only be opened by the Windows service account under which it was created or by a principal with access to both the service account name and its password.</span></span>  
  
 <span data-ttu-id="541a4-107">サービス マスター キーを再生成または復元するには、完全な暗号化階層の暗号化解除と再暗号化が必要になります。</span><span class="sxs-lookup"><span data-stu-id="541a4-107">Regenerating or restoring the Service Master Key involves decrypting and re-encrypting the complete encryption hierarchy.</span></span> <span data-ttu-id="541a4-108">この操作ではリソースが集中的に使用されるので、キーが侵害されている場合を除いて、業務が忙しい時間帯を避けてスケジュールを設定するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="541a4-108">Unless the key has been compromised, this resource-intensive operation should be scheduled during a period of low demand.</span></span>  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] <span data-ttu-id="541a4-109">AES 暗号化アルゴリズムを使用してサービス マスター キー (SMK) とデータベース マスター キー (DMK) を保護します。</span><span class="sxs-lookup"><span data-stu-id="541a4-109">uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="541a4-110">AES は、以前のバージョンで使用されていた 3DES よりも新しい暗号化アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="541a4-110">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="541a4-111">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] のインスタンスを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] にアップグレードした後で、マスター キーを AES にアップグレードするために SMK と DMK を再度生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="541a4-111">After upgrading an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] the SMK and DMK should be regenerated in order to upgrade the master keys to AES.</span></span> <span data-ttu-id="541a4-112">SMK の再作成の詳細については、「[ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql)」および「[ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="541a4-112">For more information about regenerating the SMK, see [ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-service-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="541a4-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="541a4-113">Best Practice</span></span>  
 <span data-ttu-id="541a4-114">サービス マスター キーをバックアップし、バックアップしたコピーをセキュリティで保護されたオフサイトの場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="541a4-114">Back up the Service Master Key and store the backed up copy in a secure, off-site location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="541a4-115">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="541a4-115">Related Tasks</span></span>  
 [<span data-ttu-id="541a4-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="541a4-116">BACKUP SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-service-master-key-transact-sql)  
  
 [<span data-ttu-id="541a4-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="541a4-117">RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-service-master-key-transact-sql)  
  
 [<span data-ttu-id="541a4-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="541a4-118">ALTER SERVICE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-service-master-key-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="541a4-119">参照</span><span class="sxs-lookup"><span data-stu-id="541a4-119">See Also</span></span>  
 [<span data-ttu-id="541a4-120">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="541a4-120">Encryption Hierarchy</span></span>](encryption-hierarchy.md)  
  
  
