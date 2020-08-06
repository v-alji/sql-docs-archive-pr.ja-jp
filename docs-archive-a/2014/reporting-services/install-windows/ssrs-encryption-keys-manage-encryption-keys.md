---
title: 暗号化キーの構成と管理 (SSRS 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: afe9edff22c67b9b27c1fca88c9413f5a9ed98de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742938"
---
# <a name="configure-and-manage-encryption-keys-ssrs-configuration-manager"></a><span data-ttu-id="6e7bd-102">暗号化キーの構成と管理 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="6e7bd-102">Configure and Manage Encryption Keys (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6e7bd-103">では、暗号化キーを使用して、レポート サーバー データベースに格納されている資格情報および接続情報をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-103">uses encryption keys to secure credentials and connection information that is stored in a report server database.</span></span> <span data-ttu-id="6e7bd-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の暗号化では、公開キー、秘密キー、対称キーを組み合わせて機密データの保護に使用します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-104">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], encryption is supported through a combination of public, private, and symmetric keys that are used to protect sensitive data.</span></span> <span data-ttu-id="6e7bd-105">対称キーは、レポート サーバーをインストールまたは構成するとき、レポート サーバーの初期化中に作成されます。レポート サーバーはこの対称キーを使用して、レポート サーバーに保存される機密データを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-105">The symmetric key is created during report server initialization when you install or configure the report server, and it is used by the report server to encrypt sensitive data that is stored in the report server.</span></span> <span data-ttu-id="6e7bd-106">公開キーと秘密キーはオペレーティング システムによって作成され、これらのキーを使用して対称キーが保護されます。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-106">Public and private keys are created by the operating system, and they are used to protect the symmetric key.</span></span> <span data-ttu-id="6e7bd-107">公開キーと秘密キーのペアは、レポート サーバー データベースに機密データを格納するレポート サーバー インスタンスごとに作成されます。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-107">A public and private key pair is created for each report server instance that stores sensitive data in a report server database.</span></span>  
  
 <span data-ttu-id="6e7bd-108">暗号化キーを管理するには、対称キーのバックアップ コピーを作成するほか、キーの復元、削除、変更のタイミングと方法を知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-108">Managing the encryption keys consists of creating a backup copy of the symmetric key, and knowing when and how to restore, delete, or change the keys.</span></span> <span data-ttu-id="6e7bd-109">レポート サーバーのインストールを移行する場合、またはスケールアウト配置を構成する場合は、対称キーを新しいインストールに適用できるように、対称キーのバックアップ コピーが必要です。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-109">If you migrate a report server installation or configure a scale-out deployment, you must have a backup copy of the symmetric key so that you can apply it to the new installation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6e7bd-110">セキュリティを高めるために、Reporting Services の暗号化キーは定期的に変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-110">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="6e7bd-111">キーを変更する推奨されるタイミングは、Reporting Services のメジャー バージョンのアップグレードの直後です。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-111">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="6e7bd-112">アップグレード後であれば、アップグレード サイクル以外での Reporting Services の暗号化キーの変更に伴う他のサービスの中断を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-112">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="6e7bd-113">対称キーを管理する場合、Reporting Services 構成ツールまたは **rskeymgmt** ユーティリティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-113">To manage symmetric keys, you can use the Reporting Services Configuration tool or the **rskeymgmt** utility.</span></span> <span data-ttu-id="6e7bd-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に含まれるツールは、対称キーのみの管理に使用します (公開キーと秘密キーはオペレーティング システムによって管理されます)。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-114">The tools included in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are used to manage the symmetric key only (the public and private keys are managed by the operating system).</span></span> <span data-ttu-id="6e7bd-115">Reporting Services 構成ツールと **rskeymgmt** ユーティリティはどちらも、以下のタスクをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-115">Both the Reporting Services Configuration tool and the **rskeymgmt** utility support the following tasks:</span></span>  
  
-   <span data-ttu-id="6e7bd-116">レポート サーバーを復旧させるため、または計画的な移行の一環として使用できるように、対称キーのコピーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-116">Back up a copy of the symmetric key so that you can use it to recover a report server installation or as part of a planned migration.</span></span>  
  
-   <span data-ttu-id="6e7bd-117">以前保存した対称キーをレポート サーバー データベースに復元し、新しいレポート サーバー インスタンスによって暗号化されたわけではない既存のデータにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-117">Restore a previously saved symmetric key to a report server database, allowing a new report server instance to access existing data that it did not originally encrypt.</span></span>  
  
-   <span data-ttu-id="6e7bd-118">暗号化されたデータにアクセスできなくなった場合は、レポート サーバー データベース内の暗号化されたデータを削除します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-118">Delete the encrypted data in a report server database in the unlikely event that you can no longer access encrypted data.</span></span>  
  
-   <span data-ttu-id="6e7bd-119">対称キーに障害が起きた場合は、その対称キーを再作成し、データを再暗号化します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-119">Re-create symmetric keys and re-encrypt data in the unlikely event that the symmetric key is compromised.</span></span> <span data-ttu-id="6e7bd-120">セキュリティを重視する場合は、対称キーを定期的 (たとえば、数か月ごと) に再作成して、キーを解読しようとするサイバー攻撃からレポート サーバー データベースを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-120">As a security best practice, you should recreate the symmetric key periodically (for example, every few months) to protect the report server database from cyber attacks that attempt to decipher the key.</span></span>  
  
-   <span data-ttu-id="6e7bd-121">複数のレポート サーバーが 1 つのレポート サーバー データベースとそのデータベースの暗号化を解除する対称キーの両方を共有する場合、スケールアウト配置のレポート サーバーでレポート サーバーのインスタンスを追加、または削除します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-121">Add or remove a report server instance from a report server scale-out deployment where multiple report servers share both a single report server database and the symmetric key that provides reversible encryption for that database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e7bd-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6e7bd-122">In This Section</span></span>  
 [<span data-ttu-id="6e7bd-123">レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7bd-123">Initialize a Report Server &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-initialize-a-report-server.md)  
 <span data-ttu-id="6e7bd-124">暗号化キーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-124">Explains how encryption keys are created.</span></span>  
  
 [<span data-ttu-id="6e7bd-125">Reporting Services の暗号化キーのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="6e7bd-125">Back Up and Restore Reporting Services Encryption Keys</span></span>](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 <span data-ttu-id="6e7bd-126">暗号化キーをバックアップおよび復元し、レポート サーバーを復旧または移行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-126">Explains how to back up encryption keys and restore them to recover or migrate a report server installation.</span></span>  
  
 [<span data-ttu-id="6e7bd-127">暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7bd-127">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 <span data-ttu-id="6e7bd-128">レポート サーバーでの暗号化について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-128">Describes encryption on a report server.</span></span>  
  
 [<span data-ttu-id="6e7bd-129">暗号化キーの削除と再作成  &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7bd-129">Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 <span data-ttu-id="6e7bd-130">対称キーを新しいバージョンに置き換える方法、および対称キーを検証できない場合にやり直す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-130">Explains how you can replace a symmetric key with a new version, and how to start over if symmetric keys cannot be validated.</span></span>  
  
 [<span data-ttu-id="6e7bd-131">スケールアウト配置に関する暗号化キーの追加と削除 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7bd-131">Add and Remove Encryption Keys for Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 <span data-ttu-id="6e7bd-132">暗号化キーを追加および削除し、どのレポート サーバーをスケールアウト配置の一部に含めるのかを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e7bd-132">Explains how to add and remove encryption keys to control which report servers are part of a scale-out deployment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7bd-133">参照</span><span class="sxs-lookup"><span data-stu-id="6e7bd-133">See Also</span></span>  
 [<span data-ttu-id="6e7bd-134">暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="6e7bd-134">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
