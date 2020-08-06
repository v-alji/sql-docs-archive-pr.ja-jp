---
title: Azure Key Vault を使用する拡張キー管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 0e4bbc4f0c371c927988e6b91fdbf47307ad9d3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743173"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a><span data-ttu-id="52fbc-102">Azure Key Vault を使用する拡張キー管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52fbc-102">Extensible Key Management Using Azure Key Vault (SQL Server)</span></span>
  <span data-ttu-id="52fbc-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Azure Key Vault 用のコネクタを [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] すると、暗号化キーを保護するための[拡張キー管理 &#40;EKM&#41;](extensible-key-management-ekm.md)プロバイダーとして Azure Key Vault サービスを利用できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to leverage the Azure Key Vault service as an [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) provider to protect its encryption keys.</span></span>

 <span data-ttu-id="52fbc-104">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="52fbc-104">Included in this topic:</span></span>

-   [<span data-ttu-id="52fbc-105">EKM の使用</span><span class="sxs-lookup"><span data-stu-id="52fbc-105">Uses of EKM</span></span>](#Uses)

-   [<span data-ttu-id="52fbc-106">手順 1:SQL Server で使用する Key Vault の設定</span><span class="sxs-lookup"><span data-stu-id="52fbc-106">Step 1: Setting up the Key Vault for use by SQL Server</span></span>](#Step1)

-   [<span data-ttu-id="52fbc-107">手順 2:SQL Server コネクタのインストール</span><span class="sxs-lookup"><span data-stu-id="52fbc-107">Step 2: Installing the SQL Server Connector</span></span>](#Step2)

-   [<span data-ttu-id="52fbc-108">手順 3:EKM プロバイダーを Key Vault に使用する SQL Server の構成</span><span class="sxs-lookup"><span data-stu-id="52fbc-108">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>](#Step3)

-   [<span data-ttu-id="52fbc-109">例 A:Key Vault からの非対称キーを使用した透過的データ暗号化</span><span class="sxs-lookup"><span data-stu-id="52fbc-109">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleA)

-   [<span data-ttu-id="52fbc-110">例 B:Key Vault からの非対称キーを使用したバックアップの暗号化</span><span class="sxs-lookup"><span data-stu-id="52fbc-110">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleB)

-   [<span data-ttu-id="52fbc-111">例 C:Key Vault からの非対称キーを使用した列レベルの暗号化</span><span class="sxs-lookup"><span data-stu-id="52fbc-111">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>](#ExampleC)

##  <a name="uses-of-ekm"></a><a name="Uses"></a><span data-ttu-id="52fbc-112">EKM の使用</span><span class="sxs-lookup"><span data-stu-id="52fbc-112">Uses of EKM</span></span>
 <span data-ttu-id="52fbc-113">組織では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化を使用して秘密データを保護できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-113">An organization can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption to protect sensitive data.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="52fbc-114">暗号化には、 [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md)、[列レベルの暗号化](/sql/t-sql/functions/cryptographic-functions-transact-sql)(CLE)、および[バックアップの暗号化](../../backup-restore/backup-encryption.md)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-114">encryption includes [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), [Column Level Encryption](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE), and [Backup Encryption](../../backup-restore/backup-encryption.md).</span></span> <span data-ttu-id="52fbc-115">これらのすべてのケースでは、対称なデータ暗号化キーを使用してデータが暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-115">In all of these cases the data is encrypted using a symmetric data encryption key.</span></span> <span data-ttu-id="52fbc-116">対称なデータ暗号化キーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に格納されたキーの階層で暗号化することにより、さらに保護されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-116">The symmetric data encryption key is further protected by encrypting it with a hierarchy of keys stored in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52fbc-117">それに対して、EKM プロバイダーのアーキテクチャでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の外側にある外部暗号化サービス プロバイダーに格納された非対称キーを使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でデータの暗号化キーを保護できるようにします。</span><span class="sxs-lookup"><span data-stu-id="52fbc-117">Alternatively, the EKM provider architecture enables [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to protect the data encryption keys by using an asymmetric key stored outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in an external cryptographic provider.</span></span> <span data-ttu-id="52fbc-118">EKM プロバイダーのアーキテクチャを使用すると、さらにセキュリティ層を追加し、組織の中でキーとデータの管理を分離できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-118">Using EKM provider architecture adds an additional layer of security and allows organizations to separate the management of keys and data.</span></span>

 <span data-ttu-id="52fbc-119">Azure Key Vault 用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタを使用すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は暗号化キーを保護する EKM プロバイダーとして拡張性、パフォーマンス、および可用性の高い Key Vault サービスを利用できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector for Azure Key Vault lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leverage the scalable, high performance, and highly available key vault service as an EKM provider for encryption key protection.</span></span> <span data-ttu-id="52fbc-120">Key Vault サービスは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Azure Virtual Machines 上の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インストール環境で使用したり、オンプレミス サーバー用に使用したりすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-120">The key vault service can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installations on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Virtual Machines and for on-premises servers.</span></span> <span data-ttu-id="52fbc-121">また、資格情報コンテナー サービスでは、厳密な管理および監視下にあるハードウェア セキュリティ モジュール (HSM) を使用し、非対称暗号化キーをより高いレベルで保護するオプションも提供します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-121">The key vault service also provides the option to use tightly controlled and monitored Hardware Security Modules (HSMs) for a higher level of protection for asymmetric encryption keys.</span></span> <span data-ttu-id="52fbc-122">資格情報コンテナーの詳細については、「 [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-122">For more information about the key vault, see [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).</span></span>

 <span data-ttu-id="52fbc-123">次の図は、Key Vault を使用した EKM のプロセス フローについてまとためものです。</span><span class="sxs-lookup"><span data-stu-id="52fbc-123">The following image summarizes the process flow of EKM using the key vault.</span></span> <span data-ttu-id="52fbc-124">図の中にプロセス手順番号が示されていますが、図の後に示す設定手順の番号と対応しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52fbc-124">The process step numbers in the image are not meant to match the setup step numbers that follow the image.</span></span>

 <span data-ttu-id="52fbc-125">![Azure Key Vault を使用した SQL Server EKM](../../../database-engine/media/ekm-using-azure-key-vault.png "Azure Key Vault を使用した SQL Server EKM")</span><span class="sxs-lookup"><span data-stu-id="52fbc-125">![SQL Server EKM using the Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "SQL Server EKM using the Azure Key Vault")</span></span>

##  <a name="step-1-set-up-the-key-vault-for-use-by-sql-server"></a><a name="Step1"></a><span data-ttu-id="52fbc-126">手順 1: SQL Server で使用する Key Vault を設定する</span><span class="sxs-lookup"><span data-stu-id="52fbc-126">Step 1: Set up the Key Vault for use by SQL Server</span></span>
 <span data-ttu-id="52fbc-127">次の手順では、暗号化キーを保護するために [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] で使用する資格情報コンテナーを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-127">Use the following steps to set up a key vault for use with the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] for encryption key protection.</span></span> <span data-ttu-id="52fbc-128">コンテナーは、組織内で既に使用中になっていることもあります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-128">A vault may already be in use for the organization.</span></span> <span data-ttu-id="52fbc-129">資格情報コンテナーが存在しない場合は、暗号化キーを管理するように指名された組織内の Azure 管理者がコンテナーを作成し、コンテナー内に非対称キーを生成し、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によるキー使用を許可します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-129">When a vault does not exist, the Azure Administrator in your organization that is designated to manage encryption keys can create a vault, generate an asymmetric key in the vault, and then authorize [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use the key.</span></span> <span data-ttu-id="52fbc-130">Key Vault サービスについて習熟するため、「 [Azure Key Vault の使用を開始する](https://go.microsoft.com/fwlink/?LinkId=521402)」と、PowerShell の「 [Azure Key Vault のコマンドレット](https://docs.microsoft.com/powershell/module/azurerm.keyvault) 」をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-130">To familiarize yourself with the key vault service review [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402), and the PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="52fbc-131">複数の Azure サブスクリプションがある場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を含むサブスクリプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-131">If you have multiple Azure subscriptions, you must use the subscription that contains [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

1.  <span data-ttu-id="52fbc-132">**コンテナーを作成する:** 「 **Azure Key Vault の使用を開始する** 」の「 [Key Vault の作成](https://go.microsoft.com/fwlink/?LinkId=521402)」セクションにある指示に従って資格情報コンテナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-132">**Create a vault:** Create a vault by using the instructions in the **Create a key vault** section of [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="52fbc-133">コンテナーの名前を記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-133">Record the name of the vault.</span></span> <span data-ttu-id="52fbc-134">このトピックでは、" **ContosoKeyVault** " という資格情報コンテナー名を使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-134">This topic uses **ContosoKeyVault** as the key vault name.</span></span>

2.  <span data-ttu-id="52fbc-135">**コンテナー内に非対称キーを生成する:** 資格情報コンテナー内の非対称キーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化キーを保護するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-135">**Generate an asymmetric key in the vault:** The asymmetric key in the key vault is used to protect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption keys.</span></span> <span data-ttu-id="52fbc-136">資格情報コンテナーから出て行くのは非対称キーの公開部分だけで、秘密の部分がコンテナーからエクスポートされることはありません。</span><span class="sxs-lookup"><span data-stu-id="52fbc-136">Only the public portion of the asymmetric key ever leaves the vault, the private portion is never exported by the vault.</span></span> <span data-ttu-id="52fbc-137">非対称キーを使用するすべての暗号化操作は、Azure Key Vault に委任され、資格情報コンテナーのセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-137">All cryptographic operations using the asymmetric key are delegated to the Azure Key Vault, and are protected by the key vault security.</span></span>

     <span data-ttu-id="52fbc-138">非対称キーを生成して資格情報コンテナーに格納する方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-138">There are several ways that you can generate an asymmetric key and store it in the vault.</span></span> <span data-ttu-id="52fbc-139">外部からキーを生成し、キーを .pfx ファイルとして資格情報コンテナーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="52fbc-139">You can externally generate a key, and import the key into the vault as a .pfx file.</span></span> <span data-ttu-id="52fbc-140">または、Key Vault の API を使用してキーを直接資格情報コンテナーに作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-140">Or create the key directly in the vault by using the key vault APIs.</span></span>

     <span data-ttu-id="52fbc-141">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタでは、非対称キーを 2048 ビット RSA にする必要があり、キー名に使用できるのは文字 "a ～ z"、"A ～ Z"、"0 ～ 9"、および "-" です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-141">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector requires the asymmetric keys to be 2048-bit RSA, and the key name can only use the characters "a-z", "A-Z", "0-9", and "-".</span></span> <span data-ttu-id="52fbc-142">このドキュメントでは、非対称キーの名前を **ContosoMasterKey**とします。</span><span class="sxs-lookup"><span data-stu-id="52fbc-142">In this document the name of the asymmetric key is referred to as **ContosoMasterKey**.</span></span> <span data-ttu-id="52fbc-143">これは、キーに実際に使用する一意の名前で置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-143">Replace this with the unique name you use for the key.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="52fbc-144">実稼働のシナリオでは、非対称キーをインポートする方法を強くお勧めします。管理者は、キーをキー エスクロー システムに預託できるからです。</span><span class="sxs-lookup"><span data-stu-id="52fbc-144">Importing the asymmetric key is highly recommended for production scenarios because it allows the administrator to escrow the key in a key escrow system.</span></span> <span data-ttu-id="52fbc-145">資格情報コンテナー内で非対称キーを作成する方法の場合、秘密キーは資格情報コンテナーの外に出ることがないため、エスクローに預託することができません。</span><span class="sxs-lookup"><span data-stu-id="52fbc-145">If the asymmetric key is created in the vault, it cannot be escrowed because the private key can never leave the vault.</span></span> <span data-ttu-id="52fbc-146">重要なデータの保護に使用するキーはエスクローに預託してください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-146">Keys used to protect critical data should be escrowed.</span></span> <span data-ttu-id="52fbc-147">非対称キーを紛失すると、データが永久的に復元不能になります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-147">The loss of an asymmetric key will result in permanently unrecoverable data.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="52fbc-148">資格情報コンテナーでは、同じ名前を付けたキーの複数のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-148">The key vault supports multiple versions of the same named key.</span></span> <span data-ttu-id="52fbc-149">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタで使用するキーは、バージョン管理したりロールしたりするべきではありません。</span><span class="sxs-lookup"><span data-stu-id="52fbc-149">Keys to be used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector should not be versioned or rolled.</span></span> <span data-ttu-id="52fbc-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化に使用するキーをロールしたいと管理者が考える場合は、コンテナー内に別の名前で新しいキーを作成し、DEK を暗号化するために使用してください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-150">If the administrator wants to roll the key used for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption, a new key with a different name should be created in the vault and used to encrypt the DEK.</span></span>

     <span data-ttu-id="52fbc-151">資格情報コンテナーにキーをインポートする方法、および資格情報コンテナー内でキーを作成する方法 (実稼働環境では推奨されません) の詳細については、「 **Azure Key Vault の使用を開始する**[」の「キーまたは秘密キーを資格情報コンテナーに追加する](https://go.microsoft.com/fwlink/?LinkId=521402)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-151">For more information on how to import a key into the key vault or to create a key in the key vault (not recommended for a production environment), see the **Add a key or secret to the key vault** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

3.  <span data-ttu-id="52fbc-152">**SQL Server で使用する Azure Active Directory のサービス プリンシパルを取得する:** Microsoft クラウド サービスにサインアップする時点で、組織は Azure Active Directory を取得します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-152">**Get Azure Active Directory Service Principals to use for SQL Server:** When the organization signs up for a Microsoft cloud service, it gets an Azure Active Directory.</span></span> <span data-ttu-id="52fbc-153">**が資格情報コンテナーにアクセスする時に (Azure Active Directory に対して自身を認証するために) 使用する** サービス プリンシパル [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を Azure Active Directory 内に作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-153">Create **Service Principals** in the Azure Active Directory for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use (to authenticate itself to Azure Active Directory) while accessing the key vault.</span></span>

    -   <span data-ttu-id="52fbc-154">\*\*\*\* で暗号化を使用するよう構成するときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理者が資格情報コンテナーにアクセスするために、1 つのサービス プリンシパル [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が必要になります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-154">One **Service Principal** will be needed by a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator to access the vault while configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to use encryption.</span></span>

    -   <span data-ttu-id="52fbc-155">\*\*\*\* の暗号化で使用するラップ解除キーを取得するために [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] が資格情報コンテナーにアクセスするときに、もう 1 つのサービス プリンシパル [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が必要になります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-155">Another **Service Principal** will be needed by the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] to access the vault for unwrapping keys used in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

     <span data-ttu-id="52fbc-156">アプリケーションを登録してサービス プリンシパルを生成する方法の詳細については、「 **Azure Key Vault の使用を開始する** 」の「 [アプリケーションを Azure Active Directory に登録する](https://go.microsoft.com/fwlink/?LinkId=521402)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-156">For more information about how to register an application and generate a service principal, see the **Register an Application with Azure Active Directory** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span> <span data-ttu-id="52fbc-157">この登録プロセスからは、Azure Active Directory の **サービス プリンシパル** ごとに、 **アプリケーション ID**( **クライアント ID** とも呼ばれる) および **認証キー**( **シークレット**とも呼ばれる) が返されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-157">The registration process returns an **Application ID** (also known as a **CLIENT ID**) and a **Authentication Key** (also known as a **Secret**) for each Azure Active Directory **Service Principal**.</span></span> <span data-ttu-id="52fbc-158">ステートメントで使用する場合は、 `CREATE CREDENTIAL` **クライアント ID**からハイフンを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-158">When used in the `CREATE CREDENTIAL` statement, the hyphen must be removed from the **CLIENT ID**.</span></span> <span data-ttu-id="52fbc-159">以下のスクリプトで使用するために、これらの情報を記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-159">Record these for use in the scripts below:</span></span>

    -   <span data-ttu-id="52fbc-160">**sysadmin** のログイン用の **サービス プリンシパル** : **CLIENTID_sysadmin_login** および **SECRET_sysadmin_login**</span><span class="sxs-lookup"><span data-stu-id="52fbc-160">**Service Principal** for a **sysadmin** login: **CLIENTID_sysadmin_login** and **SECRET_sysadmin_login**</span></span>

    -   <span data-ttu-id="52fbc-161">**用の** サービス プリンシパル [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** および **SECRET_DBEngine**。</span><span class="sxs-lookup"><span data-stu-id="52fbc-161">**Service Principal** for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]: **CLIENTID_DBEngine** and **SECRET_DBEngine**.</span></span>

4.  <span data-ttu-id="52fbc-162">**Key Vault にアクセスする権限をサービス プリンシパルに付与する:** と **と** の両方の **の両方のサービス プリンシパル** は、資格情報コンテナーでの **get**, **list**, **wrapKey**, の両方の **unwrapKey** 権限を必要とします。</span><span class="sxs-lookup"><span data-stu-id="52fbc-162">**Grant Permission for the Service Principals to access the Key Vault:** Both the **CLIENTID_sysadmin_login** and **CLIENTID_DBEngineService Principals** require the **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span> <span data-ttu-id="52fbc-163">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を通してキーを作成する予定の場合は、資格情報コンテナーでの **create** 権限も付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-163">If you intend to create keys through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] you also need to grant the **create** permission in key vault.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="52fbc-164"> ユーザーは、この資格情報コンテナーに対しては、少なくとも **wrapKey** および **unwrapKey** 操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-164">Users must have at least the **wrapKey** and **unwrapKey** operations for the key vault.</span></span>

     <span data-ttu-id="52fbc-165">資格情報コンテナーに権限を付与する操作の詳細については、「 **Azure Key Vault の使用を開始する**[」の「キーまたはシークレットを使用できるようにアプリケーションを承認する](https://go.microsoft.com/fwlink/?LinkId=521402)」セクションご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-165">For more information about granting permissions to the vault, see the **Authorize the application to use the key or secret** section in [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).</span></span>

     <span data-ttu-id="52fbc-166">Azure Key Vault のドキュメントへのリンク</span><span class="sxs-lookup"><span data-stu-id="52fbc-166">Links to Azure Key Vault documentation</span></span>

    -   [<span data-ttu-id="52fbc-167">Azure Key Vault とは</span><span class="sxs-lookup"><span data-stu-id="52fbc-167">What is Azure Key Vault?</span></span>](https://go.microsoft.com/fwlink/?LinkId=521401)

    -   [<span data-ttu-id="52fbc-168">Azure Key Vault の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="52fbc-168">Get Started with Azure Key Vault</span></span>](https://go.microsoft.com/fwlink/?LinkId=521402)

    -   <span data-ttu-id="52fbc-169">PowerShell の [Azure Key Vault コマンドレット](https://docs.microsoft.com/powershell/module/azurerm.keyvault) のリファレンス</span><span class="sxs-lookup"><span data-stu-id="52fbc-169">PowerShell [Azure Key Vault Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) reference</span></span>

##  <a name="step-2-install-the-sql-server-connector"></a><a name="Step2"></a><span data-ttu-id="52fbc-170">手順 2: SQL Server コネクタをインストールする</span><span class="sxs-lookup"><span data-stu-id="52fbc-170">Step 2: Install the SQL Server Connector</span></span>
 <span data-ttu-id="52fbc-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタのダウンロードとインストールは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンピューターの管理者が行います。</span><span class="sxs-lookup"><span data-stu-id="52fbc-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is downloaded and installed by the administrator of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="52fbc-172">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタは、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=521700)からダウンロードして入手できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-172">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector is available as a download from the [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=521700).</span></span>  <span data-ttu-id="52fbc-173">" **SQL Server Connector for Microsoft Azure Key Vault**" を検索して、詳細やシステム要件、インストール方法を確認し、コネクタのダウンロードを選択し、 **[実行]** を使用してインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-173">Search for **SQL Server Connector for Microsoft Azure Key Vault**, review the details, system requirements and install instructions and choose to download the connector and start the installation using **Run**.</span></span> <span data-ttu-id="52fbc-174">ライセンスを確認し、ライセンスに同意して続行します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-174">Review the license and accept the license and continue.</span></span>

 <span data-ttu-id="52fbc-175">既定では、コネクタは**Microsoft Azure Key Vault のために C:\Program Files\SQL Server connector**にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-175">By default the connector is installed at **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**.</span></span> <span data-ttu-id="52fbc-176">この場所は、セットアップ中に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-176">This location can be changed during setup.</span></span> <span data-ttu-id="52fbc-177">(変更した場合は、以下のスクリプトを調整してください。)</span><span class="sxs-lookup"><span data-stu-id="52fbc-177">(If changed, adjust the scripts below.)</span></span>

 <span data-ttu-id="52fbc-178">インストールを完了すると、以下のものがコンピューターにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="52fbc-178">On completing the install, the following are installed on the machine:</span></span>

-   <span data-ttu-id="52fbc-179">**Microsoft.AzureKeyVaultService.EKM.dll**:これは、CREATE CRYPTOGRAPHIC PROVIDER ステートメントを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に登録する必要のある暗号化 EKM プロバイダー DLL です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-179">**Microsoft.AzureKeyVaultService.EKM.dll**: This is the cryptographic EKM provider DLL that needs to be registered with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using the CREATE CRYPTOGRAPHIC PROVIDER statement.</span></span>

-   <span data-ttu-id="52fbc-180">**Azure Key Vault SQL Server コネクタ**:これは、暗号化 EKM プロバイダーが資格情報コンテナーと通信できるようにする Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="52fbc-180">**Azure Key Vault SQL Server Connector**: This is a Windows service that enables the cryptographic EKM provider to communicate with the key vault.</span></span>

 <span data-ttu-id="52fbc-181">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタのインストールでは、必要に応じて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化で使用するサンプル スクリプトをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-181">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector installation also allows you to optionally download sample scripts for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption.</span></span>

##  <a name="step-3-configure-sql-server-to-use-an-ekm-provider-for-the-key-vault"></a><a name="Step3"></a><span data-ttu-id="52fbc-182">手順 3: Key Vault に EKM プロバイダーを使用するように SQL Server を構成する</span><span class="sxs-lookup"><span data-stu-id="52fbc-182">Step 3: Configure SQL Server to use an EKM provider for the Key Vault</span></span>

###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="52fbc-183">Permissions</span><span class="sxs-lookup"><span data-stu-id="52fbc-183">Permissions</span></span>
 <span data-ttu-id="52fbc-184">このプロセス全体を完了するには、CONTROL SERVER 権限、または **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-184">To complete this entire process requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span> <span data-ttu-id="52fbc-185">特定のアクションで必要な権限は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="52fbc-185">Specific actions require the following permissions:</span></span>

-   <span data-ttu-id="52fbc-186">暗号化サービス プロバイダーを作成するには、CONTROL SERVER 権限、または **sysadmin** 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-186">To create a cryptographic provider, requires CONTROL SERVER permission or membership in the **sysadmin** fixed server role.</span></span>

-   <span data-ttu-id="52fbc-187">構成オプションを変更して RECONFIGURE ステートメントを実行するには、ALTER SETTINGS サーバーレベル権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-187">To change a configuration option and run the RECONFIGURE statement, you must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="52fbc-188">ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。</span><span class="sxs-lookup"><span data-stu-id="52fbc-188">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>

-   <span data-ttu-id="52fbc-189">資格情報を作成するには、ALTER ANY CREDENTIAL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-189">To create a credential, requires ALTER ANY CREDENTIAL permission.</span></span>

-   <span data-ttu-id="52fbc-190">ログインに資格情報を追加するには、ALTER ANY LOGIN 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-190">To add a credential to a login, requires ALTER ANY LOGIN permission.</span></span>

-   <span data-ttu-id="52fbc-191">非対称キーを作成するには、CREATE ASYMMETRIC KEY 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-191">To create an asymmetric key, requires CREATE ASYMMETRIC KEY permission.</span></span>

###  <a name="to-configure-sql-server-to-use-a-cryptographic-provider"></a><a name="TsqlProcedure"></a><span data-ttu-id="52fbc-192">暗号化サービスプロバイダーを使用するように SQL Server を構成するには</span><span class="sxs-lookup"><span data-stu-id="52fbc-192">To configure SQL Server to use a cryptographic provider</span></span>

1.  <span data-ttu-id="52fbc-193">EKM を使用するように [!INCLUDE[ssDE](../../../includes/ssde-md.md)] を構成し、暗号化サービス プロバイダーを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に登録 (作成) します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-193">Configure the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use EKM, and register (create) the cryptographic provider with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>

    ```sql
    -- Enable advanced options.
    USE master;
    GO

    sp_configure 'show advanced options', 1 ;
    GO
    RECONFIGURE ;
    GO
    -- Enable EKM provider
    sp_configure 'EKM provider enabled', 1 ;
    GO
    RECONFIGURE ;
    GO

    -- Create a cryptographic provider, using the SQL Server Connector
    -- which is an EKM provider for the Azure Key Vault. This example uses 
    -- the name AzureKeyVault_EKM_Prov.

    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov 
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';
    GO
    ```

2.  <span data-ttu-id="52fbc-194">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理者ログインのための [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資格情報をセットアップします。これは、資格情報コンテナーを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化のシナリオをセットアップして管理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-194">Setup a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] administrator login to use the key vault in order to setup and manage [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] encryption scenarios.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="52fbc-195">の**IDENTITY**引数には `CREATE CREDENTIAL` 、key vault 名が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-195">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="52fbc-196">の**SECRET**引数で `CREATE CREDENTIAL` は、 *\<Client ID>* (ハイフンなし) と *\<Secret>* を一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-196">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="52fbc-197">次の例では、**クライアント ID** ( `EF5C8E09-4D2A-4A76-9998-D93440D8115D` ) はハイフンを削除し、文字列として入力 `EF5C8E094D2A4A769998D93440D8115D` し、**シークレット**は*SECRET_sysadmin_login*文字列で表されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-197">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_sysadmin_login*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL sysadmin_ekm_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login' 
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;

    -- Add the credential to the SQL Server administrators domain login 
    ALTER LOGIN [<domain>/<login>]
    ADD CREDENTIAL sysadmin_ekm_cred;
    ```

     <span data-ttu-id="52fbc-198">引数に変数を使用 `CREATE CREDENTIAL` し、プログラムでクライアント ID からハイフンを削除する例については、「 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-198">For an example of using variables for the `CREATE CREDENTIAL` arguments and programmatically removing the hyphens from the Client ID, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>

3.  <span data-ttu-id="52fbc-199">以前に手順 1 のセクション 3 で説明したように非対称キーをインポートした場合は、次の例のようにキー名を提供して、キーを開きます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-199">If you imported an asymmetric key as described earlier in step 1, section 3, open the key by providing your key name in the following example.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
    CREATION_DISPOSITION = OPEN_EXISTING;
    ```

     <span data-ttu-id="52fbc-200">実稼働環境には推奨されませんが (キーをエクスポートできないため)、資格情報コンテナーで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]から直接、非対称キーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-200">Though not recommended for production (because the key cannot be exported), it is possible to create an asymmetric key directly in the vault from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52fbc-201">事前にキーをインポートしなかった場合は、次のスクリプトを使用して、テスト用に資格情報コンテナーに非対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-201">If you did not import a key earlier, then create an asymmetric key in the key vault for testing by using the following script.</span></span> <span data-ttu-id="52fbc-202">スクリプトを実行し、 **sysadmin_ekm_cred** 資格情報を使用してログインのプロビジョニングを行います。</span><span class="sxs-lookup"><span data-stu-id="52fbc-202">Execute the script, using a login provisioned with the **sysadmin_ekm_cred** credential.</span></span>

    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY 
    FROM PROVIDER [AzureKeyVault_EKM_Prov]
    WITH ALGORITHM = RSA_2048,
    PROVIDER_KEY_NAME = 'ContosoMasterKey';
    ```

> [!TIP]
>  <span data-ttu-id="52fbc-203">エラーを受信したユーザー**は、プロバイダーから公開キーをエクスポートできません。プロバイダーエラーコード: 2053。**</span><span class="sxs-lookup"><span data-stu-id="52fbc-203">Users receiving the error **Cannot export public key from the provider. Provider error code: 2053.**</span></span> <span data-ttu-id="52fbc-204">では、key vault での**get**、 **list**、 **wrapKey**、および**unwrapKey**のアクセス許可を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-204">should check their **get**, **list**, **wrapKey**, and **unwrapKey** permissions in the key vault.</span></span>

 <span data-ttu-id="52fbc-205">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="52fbc-205">For more information, see the following:</span></span>

-   [<span data-ttu-id="52fbc-206">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-206">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)

-   [<span data-ttu-id="52fbc-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-207">CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)

-   [<span data-ttu-id="52fbc-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-208">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)

-   [<span data-ttu-id="52fbc-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-209">CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-asymmetric-key-transact-sql)

-   [<span data-ttu-id="52fbc-210">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-210">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)

-   [<span data-ttu-id="52fbc-211">ALTER LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-211">ALTER LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-login-transact-sql)

## <a name="examples"></a><span data-ttu-id="52fbc-212">例</span><span class="sxs-lookup"><span data-stu-id="52fbc-212">Examples</span></span>

###  <a name="example-a-transparent-data-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleA"></a><span data-ttu-id="52fbc-213">例 A: Key Vault からの非対称キーを使用して Transparent Data Encryption する</span><span class="sxs-lookup"><span data-stu-id="52fbc-213">Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="52fbc-214">上記の手順を完了した後、資格情報とログインを作成し、資格情報コンテナー内の非対称キーで保護されたデータベース暗号化キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-214">After completing the steps above, create a credential and a login, create a database encryption key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="52fbc-215">データベース暗号化キーは、データベースを TDE で暗号化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-215">Use the database encryption key to encrypt a database with TDE.</span></span>

 <span data-ttu-id="52fbc-216">データベースを暗号化するには、データベースに対する CONTROL 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-216">To encrypt a database requires CONTROL permission on the database.</span></span>

##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a><span data-ttu-id="52fbc-217">EKM と資格情報コンテナーを使用して TDE を有効にするには</span><span class="sxs-lookup"><span data-stu-id="52fbc-217">To enable TDE using EKM and the Key Vault</span></span>

1.  <span data-ttu-id="52fbc-218">データベースの読み込み中に資格情報コンテナー EKM にアクセスするために [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が使用する [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-218">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] credential for the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to use when accessing the key vault EKM during database load.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="52fbc-219">の**IDENTITY**引数には `CREATE CREDENTIAL` 、key vault 名が必要です。</span><span class="sxs-lookup"><span data-stu-id="52fbc-219">The **IDENTITY** argument of `CREATE CREDENTIAL` requires the key vault name.</span></span> <span data-ttu-id="52fbc-220">の**SECRET**引数で `CREATE CREDENTIAL` は、 *\<Client ID>* (ハイフンなし) と *\<Secret>* を一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-220">The **SECRET** argument of `CREATE CREDENTIAL` requires the *\<Client ID>* (without hyphens) and *\<Secret>* to be passed together without a space between them.</span></span>

     <span data-ttu-id="52fbc-221">次の例で、 **クライアント ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) はハイフンを削除した文字列 `EF5C8E094D2A4A769998D93440D8115D` として入力し、 **シークレット** は文字列 *SECRET_DBEngine*として入力しています。</span><span class="sxs-lookup"><span data-stu-id="52fbc-221">In the following example, the **Client ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) is stripped of the hyphens and entered as the string `EF5C8E094D2A4A769998D93440D8115D` and the **Secret** is represented by the string *SECRET_DBEngine*.</span></span>

    ```sql
    USE master;
    CREATE CREDENTIAL Azure_EKM_TDE_cred 
        WITH IDENTITY = 'ContosoKeyVault', 
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine' 
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;
    ```

2.  <span data-ttu-id="52fbc-222">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が TDE のために使用する [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ログイン名を作成し、それに資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-222">Create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login to be used by the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] for TDE, and add the credential to it.</span></span> <span data-ttu-id="52fbc-223">この例では、 [手順 3 のセクション 3](#Step3) の説明に従って以前にマスター データベースにインポートまたは作成した、資格情報コンテナーに格納されている CONTOSO_KEY 非対称キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-223">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier for the master database, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE master;
    -- Create a SQL Server login associated with the asymmetric key 
    -- for the Database engine to use when it loads a database 
    -- encrypted by TDE.
    CREATE LOGIN TDE_Login 
    FROM ASYMMETRIC KEY CONTOSO_KEY;
    GO 

    -- Alter the TDE Login to add the credential for use by the 
    -- Database Engine to access the key vault
    ALTER LOGIN TDE_Login 
    ADD CREDENTIAL Azure_EKM_TDE_cred ;
    GO
    ```

3.  <span data-ttu-id="52fbc-224">TDE に使用するデータベース暗号化キー (DEK) を作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-224">Create the database encryption key (DEK) that will be used for TDE.</span></span> <span data-ttu-id="52fbc-225">DEK は、SQL Server でサポートされている任意のアルゴリズムまたはキーの長さを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-225">The DEK can be created using any SQL Server supported algorithm or key length.</span></span> <span data-ttu-id="52fbc-226">DEK は、資格情報コンテナー内の非対称キーによって保護されます。</span><span class="sxs-lookup"><span data-stu-id="52fbc-226">The DEK will be protected by the asymmetric key in the key vault.</span></span>

     <span data-ttu-id="52fbc-227">この例では、 [手順 3 のセクション 3](#Step3) の説明に従って以前にインポートまたは作成した、資格情報コンテナーに格納されている CONTOSO_KEY 非対称キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-227">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span>

    ```sql
    USE ContosoDatabase;
    GO

    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_128 
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;
    GO

    -- Alter the database to enable transparent data encryption.
    ALTER DATABASE ContosoDatabase 
    SET ENCRYPTION ON ;
    GO
    ```

     <span data-ttu-id="52fbc-228">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="52fbc-228">For more information, see the following:</span></span>

    -   [<span data-ttu-id="52fbc-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-229">CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-encryption-key-transact-sql)

    -   [<span data-ttu-id="52fbc-230">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="52fbc-230">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)

###  <a name="example-b-encrypting-backups-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleB"></a><span data-ttu-id="52fbc-231">例 B: Key Vault からの非対称キーを使用してバックアップを暗号化する</span><span class="sxs-lookup"><span data-stu-id="52fbc-231">Example B: Encrypting Backups by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="52fbc-232">[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]以降では、バックアップの暗号化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="52fbc-232">Encrypted backups are supported starting with [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="52fbc-233">次の例では、資格情報コンテナー内の非対称キーで保護したデータ暗号化キーによって暗号化したバックアップを作成し、復元します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-233">The following example creates and restores a backup encrypted a data encryption key protected by the asymmetric key in the key vault.</span></span>

```sql
USE master;
BACKUP DATABASE [DATABASE_TO_BACKUP]
TO DISK = N'[PATH TO BACKUP FILE]' 
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD, 
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);
GO
```

 <span data-ttu-id="52fbc-234">復元のサンプル コードです。</span><span class="sxs-lookup"><span data-stu-id="52fbc-234">Sample restore code.</span></span>

```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;
GO
```

 <span data-ttu-id="52fbc-235">バックアップオプションの詳細については、「 [backup &#40;transact-sql&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52fbc-235">For more information about backup options, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>

###  <a name="example-c-column-level-encryption-by-using-an-asymmetric-key-from-the-key-vault"></a><a name="ExampleC"></a><span data-ttu-id="52fbc-236">例 C: Key Vault からの非対称キーを使用した列レベルの暗号化</span><span class="sxs-lookup"><span data-stu-id="52fbc-236">Example C: Column Level Encryption by Using an Asymmetric Key from the Key Vault</span></span>
 <span data-ttu-id="52fbc-237">次の例では、資格情報コンテナー内の非対称キーによって保護された対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-237">The following example creates a symmetric key protected by the asymmetric key in the key vault.</span></span> <span data-ttu-id="52fbc-238">その後、その対称キーを使用してデータベース内のデータを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-238">Then the symmetric key is used to encrypt data in the database.</span></span>

 <span data-ttu-id="52fbc-239">この例では、 [手順 3 のセクション 3](#Step3) の説明に従って以前にインポートまたは作成した、資格情報コンテナーに格納されている CONTOSO_KEY 非対称キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="52fbc-239">This example uses the CONTOSO_KEY asymmetric key stored in the key vault, which was imported or created earlier, as described in [Step 3, section 3](#Step3) above.</span></span> <span data-ttu-id="52fbc-240">この非対称キーを `ContosoDatabase` データベースで使用するには、CREATE ASYMMETRIC KEY ステートメントをもう一度実行して、 `ContosoDatabase` データベースにキーへの参照を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52fbc-240">To use this asymmetric key in the `ContosoDatabase` database, you must execute the CREATE ASYMMETRIC KEY statement again, to provide the `ContosoDatabase` database with a reference to the key.</span></span>

```sql
USE [ContosoDatabase];
GO

-- Create a reference to the key in the key vault
CREATE ASYMMETRIC KEY CONTOSO_KEY 
FROM PROVIDER [AzureKeyVault_EKM_Prov]
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',
CREATION_DISPOSITION = OPEN_EXISTING;

-- Create the data encryption key.
-- The data encryption key can be created using any SQL Server 
-- supported algorithm or key length.
-- The DEK will be protected by the asymmetric key in the key vault

CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY
    WITH ALGORITHM=AES_256
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

DECLARE @DATA VARBINARY(MAX);

--Open the symmetric key for use in this session
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY 
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;

--Encrypt syntax
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));

-- Decrypt syntax
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));

--Close the symmetric key
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;
```

## <a name="see-also"></a><span data-ttu-id="52fbc-241">参照</span><span class="sxs-lookup"><span data-stu-id="52fbc-241">See Also</span></span>
 <span data-ttu-id="52fbc-242">Create encryption [PROVIDER &#40;transact-sql&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [Create CREDENTIAL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [create 非対称](/sql/t-sql/statements/create-asymmetric-key-transact-sql)KEY &#40;transact-sql&#41;create [SYMMETRIC key](/sql/t-sql/statements/create-symmetric-key-transact-sql) &#40;TRANSACT-SQL&#41;[拡張キー管理 &#40;EKM&#41;](extensible-key-management-ekm.md) ekm[バックアップ暗号化](../../backup-restore/backup-encryption.md)[を使用して tde を有効にする](enable-tde-on-sql-server-using-ekm.md)[暗号化されたバックアップを作成](../../backup-restore/create-an-encrypted-backup.md)する</span><span class="sxs-lookup"><span data-stu-id="52fbc-242">[CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql) [Extensible Key Management &#40;EKM&#41;](extensible-key-management-ekm.md) [Enable TDE Using EKM](enable-tde-on-sql-server-using-ekm.md) [Backup Encryption](../../backup-restore/backup-encryption.md) [Create an Encrypted Backup](../../backup-restore/create-an-encrypted-backup.md)</span></span>
