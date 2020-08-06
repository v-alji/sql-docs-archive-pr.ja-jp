---
title: デジタル証明書を使用してパッケージに署名する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- digital signatures [Integration Services]
- signing packages [Integration Services]
- signatures [Integration Services]
ms.assetid: 182b115e-0fe2-4717-8dff-183f9eb6e397
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bd0f73d609623f882e474c96a01cd3bc0274b6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742358"
---
# <a name="sign-a-package-by-using-a-digital-certificate"></a><span data-ttu-id="c7857-102">デジタル証明書を使用してパッケージに署名する</span><span class="sxs-lookup"><span data-stu-id="c7857-102">Sign a Package by Using a Digital Certificate</span></span>
  <span data-ttu-id="c7857-103">このトピックでは、デジタル証明書を使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージに署名する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7857-103">This topic describes how to sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package with a digital certificate.</span></span> <span data-ttu-id="c7857-104">デジタル署名を他の設定と共に使用して、有効でないパッケージの読み込みや実行を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="c7857-104">You can use a digital signature, together with other settings, to prevent a package that is not valid from loading and running.</span></span>  
  
 <span data-ttu-id="c7857-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージに署名する前に、次のタスクを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7857-105">Before you can sign an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you must do the following tasks:</span></span>  
  
-   <span data-ttu-id="c7857-106">証明書と関連付ける秘密キーを作成または取得して、この秘密キーをローカル コンピューターに格納します。</span><span class="sxs-lookup"><span data-stu-id="c7857-106">Create or obtain a private key to associate with the certificate, and store this private key on the local computer.</span></span>  
  
-   <span data-ttu-id="c7857-107">信頼できる証明機関からコード署名用の証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="c7857-107">Obtain a certificate for the purpose of code signing from a trusted certification authority.</span></span> <span data-ttu-id="c7857-108">証明書を取得または作成するには、次のいずれかの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c7857-108">You can use one of the following methods to obtain or create a certificate:</span></span>  
  
    -   <span data-ttu-id="c7857-109">証明書を発行する公的な商用証明機関から証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="c7857-109">Obtain a certificate from a public, commercial certification authority that issues certificates.</span></span>  
  
    -   <span data-ttu-id="c7857-110">組織が証明書を内部的に発行できるようにする証明書サーバーから証明書を入手します。</span><span class="sxs-lookup"><span data-stu-id="c7857-110">Obtain a certificate from a certificate server, that enables an organization to internally issue certificates.</span></span> <span data-ttu-id="c7857-111">証明書の署名に使用されるルート証明書を、 **[信頼されたルート証明機関]** ストアに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7857-111">You have to add the root certificate that is used to sign the certificate to the **Trusted Root Certification Authorities** store.</span></span> <span data-ttu-id="c7857-112">ルート証明書を追加するには、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 管理コンソール (MMC) の証明書スナップインを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7857-112">To add the root certificate, you can use the Certificates snap-in for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="c7857-113">詳細については、MSDN ライブラリの「[証明書サービス](https://go.microsoft.com/fwlink/?LinkId=100755)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7857-113">For more information, see the topic, "[Certificate Services](https://go.microsoft.com/fwlink/?LinkId=100755)," in the MSDN library.</span></span>  
  
    -   <span data-ttu-id="c7857-114">テスト目的でのみ独自の証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="c7857-114">Create your own certificate for testing purposes only.</span></span> <span data-ttu-id="c7857-115">証明書作成ツール (Makecert.exe) は、テスト目的で X.509 証明書を生成します。</span><span class="sxs-lookup"><span data-stu-id="c7857-115">The Certificate Creation Tool (Makecert.exe) generates X.509 certificates for testing purposes.</span></span> <span data-ttu-id="c7857-116">詳細については、MSDN ライブラリの「[証明書作成ツール (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7857-116">For more information, see the topic, "[Certificate Creation Tool (Makecert.exe)](https://go.microsoft.com/fwlink/?LinkId=100756)," in the MSDN Library.</span></span>  
  
     <span data-ttu-id="c7857-117">証明書の詳細については、証明書スナップインのオンライン ヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7857-117">For more information about certificates, see the online Help for the Certificates snap-in.</span></span> <span data-ttu-id="c7857-118">デジタル アセットの署名方法の詳細については、MSDN ライブラリの「[Authenticode を使用したコードの署名と検証](https://go.microsoft.com/fwlink/?LinkId=78100)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7857-118">For more information about how to sign digital assets, see the topic, "[Signing and Checking Code with Authenticode](https://go.microsoft.com/fwlink/?LinkId=78100)," in the MSDN Library.</span></span>  
  
-   <span data-ttu-id="c7857-119">証明書がコードの署名用に有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c7857-119">Make sure that the certificate has been enabled for code signing.</span></span> <span data-ttu-id="c7857-120">証明書がコードの署名用に有効になっているかどうかを判断するには、証明書スナップインで証明書のプロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="c7857-120">To determine whether a certificate is enabled for code signing, review the properties of the certificate in the Certificates snap-in.</span></span>  
  
-   <span data-ttu-id="c7857-121">個人ストアに証明書を格納します。</span><span class="sxs-lookup"><span data-stu-id="c7857-121">Store the certificate in the Personal store.</span></span>  
  
 <span data-ttu-id="c7857-122">上記のタスクが完了したら、次の手順に従ってパッケージに署名できます。</span><span class="sxs-lookup"><span data-stu-id="c7857-122">After you have completed the previous tasks, you can use the following procedure to sign a package.</span></span>  
  
### <a name="to-sign-a-package"></a><span data-ttu-id="c7857-123">パッケージに署名するには</span><span class="sxs-lookup"><span data-stu-id="c7857-123">To sign a package</span></span>  
  
1.  <span data-ttu-id="c7857-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、署名するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c7857-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to be signed.</span></span>  
  
2.  <span data-ttu-id="c7857-125">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c7857-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c7857-126">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで **[SSIS]** メニューの **[デジタル署名]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7857-126">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, on the **SSIS** menu, click **Digital Signing**.</span></span>  
  
4.  <span data-ttu-id="c7857-127">**[デジタル署名]** ダイアログ ボックスで、 **[署名]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7857-127">In the **Digital Signing** dialog box, click **Sign**.</span></span>  
  
5.  <span data-ttu-id="c7857-128">**[証明書の選択]** ダイアログ ボックスで、証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="c7857-128">In the **Select a Certificate** dialog box, select a certificate.</span></span>  
  
6.  <span data-ttu-id="c7857-129">必要に応じて、 **[証明書の表示]** をクリックして証明書の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c7857-129">(Optional) Click **View Certificat**e to view certificate information.</span></span>  
  
7.  <span data-ttu-id="c7857-130">**[OK]** をクリックして、 **[証明書の選択]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c7857-130">Click **OK** to close the **Select a Certificate** dialog box.</span></span>  
  
8.  <span data-ttu-id="c7857-131">**[OK]** をクリックして、 **[デジタル署名]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c7857-131">Click **OK** to close the **Digital Signing** dialog box.</span></span>  
  
9. <span data-ttu-id="c7857-132">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7857-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
     <span data-ttu-id="c7857-133">パッケージは署名されましたが、パッケージを読み込む前にデジタル署名を確認するように、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7857-133">Although the package has been signed, you must now configure [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to check or verify the digital signature before loading the package.</span></span> <span data-ttu-id="c7857-134">詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](security/identify-the-source-of-packages-with-digital-signatures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7857-134">For more information, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7857-135">参照</span><span class="sxs-lookup"><span data-stu-id="c7857-135">See Also</span></span>  
 [<span data-ttu-id="c7857-136">セキュリティの概要 &#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c7857-136">Security Overview &#40;Integration Services&#41;</span></span>](security/security-overview-integration-services.md)  
  
  
