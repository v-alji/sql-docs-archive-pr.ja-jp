---
title: 暗号化されたミラー データベースの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5148411792f1ea881bba59e599252284575bbdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716726"
---
# <a name="set-up-an-encrypted-mirror-database"></a><span data-ttu-id="65fc2-102">暗号化されたミラー データベースの設定</span><span class="sxs-lookup"><span data-stu-id="65fc2-102">Set Up an Encrypted Mirror Database</span></span>

<span data-ttu-id="65fc2-103">ミラー データベースのデータベース マスター キーの暗号化を自動的に解除できるようにするには、マスター キーの暗号化に使用したパスワードをミラー サーバー インスタンスに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65fc2-103">To enable automatic decryption of the database master key of a mirror database, you must provide the password used to encrypt the master key to the mirror server instance.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="65fc2-104">以降のバージョンには、パスワードを転送するメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="65fc2-104">and later versions include mechanisms to transfer the password.</span></span> <span data-ttu-id="65fc2-105">データベース ミラーリングを開始する前にデータベース マスター キーに対する資格情報を作成するには、 **sp_control_dbmasterkey_password** を使用します。</span><span class="sxs-lookup"><span data-stu-id="65fc2-105">Use **sp_control_dbmasterkey_password** to create a credential for the database master key before you start database mirroring.</span></span> <span data-ttu-id="65fc2-106">この処理は、ミラー化するすべてのデータベースに対して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="65fc2-106">You must repeat this process for every database that will be mirrored.</span></span> <span data-ttu-id="65fc2-107">詳細については、「 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65fc2-107">For more information, see [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql).</span></span>
  
> [!CAUTION]  
>  <span data-ttu-id="65fc2-108">**sa** など高いレベルの特権を持つサーバー プリンシパルからのアクセスを禁止したままにしておく必要のあるデータベースについては、フェールオーバー時の暗号化解除を有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="65fc2-108">Do not enable failover decryption of a database that must remain inaccessible to **sa** and other highly privileged server principals.</span></span> <span data-ttu-id="65fc2-109">データベースのキー階層をサービス マスター キーで暗号化解除できないようにデータベースを構成できます。</span><span class="sxs-lookup"><span data-stu-id="65fc2-109">You can configure a database so that its key hierarchy cannot be decrypted by the service master key.</span></span> <span data-ttu-id="65fc2-110">このオプションは、 **sa** など特権レベルの高いサーバー プリンシパルからアクセスできてはならない情報を格納しているデータベースに対する多層防御の 1 つとしてサポートされています。</span><span class="sxs-lookup"><span data-stu-id="65fc2-110">This option is supported as a defense-in-depth for databases that contain information that should not be accessible to **sa** or other highly privileged server principals.</span></span> <span data-ttu-id="65fc2-111">このようなデータベースに対してフェールオーバー時の暗号化解除を有効にすると、この多層防御が効力を失います。その結果、 **sa** など特権レベルの高いサーバー プリンシパルによるデータベースの暗号化解除が可能になります。</span><span class="sxs-lookup"><span data-stu-id="65fc2-111">Enabling failover decryption of such a database removes this defense-in-depth, enabling **sa** and other highly privileged server principals to decrypt the database.</span></span>  


<!-- Note: We cannot append '?view=sql-server-2016' to these, even tho in theory we might want to. -->

## <a name="see-also"></a><span data-ttu-id="65fc2-112">参照</span><span class="sxs-lookup"><span data-stu-id="65fc2-112">See Also</span></span>

[<span data-ttu-id="65fc2-113">sp_control_dbmasterkey_password &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65fc2-113">sp_control_dbmasterkey_password &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql)

[<span data-ttu-id="65fc2-114">CREATE MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65fc2-114">CREATE MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-master-key-transact-sql)

[<span data-ttu-id="65fc2-115">ALTER MASTER KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="65fc2-115">ALTER MASTER KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-master-key-transact-sql)

[<span data-ttu-id="65fc2-116">暗号化階層</span><span class="sxs-lookup"><span data-stu-id="65fc2-116">Encryption Hierarchy</span></span>](../../relational-databases/security/encryption/encryption-hierarchy.md)

[<span data-ttu-id="65fc2-117">データベース ミラーリングの設定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="65fc2-117">Setting Up Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)

