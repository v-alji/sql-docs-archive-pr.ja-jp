---
title: デジタル署名を使用してパッケージのソースを特定する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90c0e2e3db13ba4b228b70ccfffddbc2ff221774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743341"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a><span data-ttu-id="d1ca7-102">デジタル署名を使用してパッケージのソースを特定する</span><span class="sxs-lookup"><span data-stu-id="d1ca7-102">Identify the Source of Packages with Digital Signatures</span></span>
  <span data-ttu-id="d1ca7-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、そのソースを識別するために、デジタル証明書を使用して署名できます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be signed with a digital certificate to identify its source.</span></span> <span data-ttu-id="d1ca7-104">パッケージがデジタル証明書を使用して署名されたら、パッケージを読み込む前に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] でデジタル署名を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-104">After a package has been signed with a digital certificate, you can have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the digital signature before loading the package.</span></span> <span data-ttu-id="d1ca7-105">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で署名を確認するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または **dtexec** ユーティリティ (dtexec.exe) でオプションを設定するか、オプションのレジストリ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-105">To have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the signature, you set an option in either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in the **dtexec** utility (dtexec.exe), or set an optional registry value.</span></span>  
  
## <a name="signing-a-package-with-a-digital-certificate"></a><span data-ttu-id="d1ca7-106">デジタル証明書を使用したパッケージの署名</span><span class="sxs-lookup"><span data-stu-id="d1ca7-106">Signing a Package with a Digital Certificate</span></span>  
 <span data-ttu-id="d1ca7-107">デジタル証明書を使用してパッケージに署名する前に、証明書を取得または作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-107">Before you can sign a package with a digital certificate, you first have to obtain or create the certificate.</span></span> <span data-ttu-id="d1ca7-108">証明書を用意したら、この証明書を使用してパッケージに署名できます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-108">After you have the certificate, you can then use this certificate to sign the package.</span></span> <span data-ttu-id="d1ca7-109">証明書を取得し、その証明書を使用してパッケージに署名する方法の詳細については、「 [デジタル証明書を使用してパッケージに署名する](../sign-a-package-by-using-a-digital-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-109">For more information about how to obtain a certificate and sign a package with that certificate, see [Sign a Package by Using a Digital Certificate](../sign-a-package-by-using-a-digital-certificate.md).</span></span>  
  
## <a name="setting-an-option-to-check-the-package-signature"></a><span data-ttu-id="d1ca7-110">パッケージの署名を確認するオプションの設定</span><span class="sxs-lookup"><span data-stu-id="d1ca7-110">Setting an Option to Check the Package Signature</span></span>  
 <span data-ttu-id="d1ca7-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と **dtexec** ユーティリティの両方に、署名付きパッケージのデジタル署名を確認するように [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を構成するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-111">Both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and the **dtexec** utility have an option that configures [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of a signed package.</span></span> <span data-ttu-id="d1ca7-112">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と **dtexec** ユーティリティのどちらを使用するかは、すべてのパッケージを確認するか特定のパッケージだけを確認するかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-112">Whether you use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or the **dtexec** utility depends on whether you want to check all packages or just specific ones:</span></span>  
  
-   <span data-ttu-id="d1ca7-113">デザイン時にすべてのパッケージのデジタル署名を確認してからパッケージを読み込むには、 **で** [パッケージの読み込み時にデジタル署名を確認する] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-113">To check the digital signature of all packages before loading the packages at design time, set the **Check digital signature when loading a package** option in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d1ca7-114">このオプションは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でのすべてのパッケージに対するグローバルな設定です。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-114">This option is a global setting for all packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d1ca7-115">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-115">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
-   <span data-ttu-id="d1ca7-116">個々のパッケージのデジタル署名を確認するには、 `/VerifyS[igned]` **dtexec**ユーティリティを使用してパッケージを実行するときにオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-116">To check the digital signature of an individual package, specify the `/VerifyS[igned]` option when you use the **dtexec** utility to run the package.</span></span> <span data-ttu-id="d1ca7-117">詳細については、「[dtexec ユーティリティ](../packages/dtexec-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-117">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a><span data-ttu-id="d1ca7-118">パッケージの署名を確認するレジストリ値の設定</span><span class="sxs-lookup"><span data-stu-id="d1ca7-118">Setting a Registry Value to Check the Package Signature</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d1ca7-119">では、オプションのレジストリ値である **BlockedSignatureStates**もサポートされています。このレジストリ値を使用すると、署名付きパッケージと署名がないパッケージの読み込みに関する組織のポリシーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-119">also supports an optional registry value, **BlockedSignatureStates**, that you can use to manage an organization's policy for loading signed and unsigned packages.</span></span> <span data-ttu-id="d1ca7-120">このレジストリ値により、パッケージが署名されていない場合、または無効な署名や信頼できない署名が含まれている場合に、パッケージが読み込まれないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-120">The registry value can prevent packages from loading if the packages are unsigned, or have invalid or untrusted signatures.</span></span> <span data-ttu-id="d1ca7-121">このレジストリ値を設定する方法の詳細については、「 [レジストリ値を設定して署名ポリシーを実装する](../implement-a-signing-policy-by-setting-a-registry-value.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-121">For more information about how to set this registry value, see [Implement a Signing Policy by Setting a Registry Value](../implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1ca7-122">オプションの **BlockedSignatureStates** レジストリ値では、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または **dtexec** コマンド ラインで設定されたデジタル署名オプションよりも制限が厳しい設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-122">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or at the **dtexec** command line.</span></span> <span data-ttu-id="d1ca7-123">この場合、制限が厳しい方のレジストリ設定が他の設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d1ca7-123">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ca7-124">参照</span><span class="sxs-lookup"><span data-stu-id="d1ca7-124">See Also</span></span>  
 <span data-ttu-id="d1ca7-125">[SSIS&#41; パッケージ &#40;Integration Services](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="d1ca7-125">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="d1ca7-126">セキュリティの概要 &#40;Integration Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d1ca7-126">Security Overview &#40;Integration Services&#41;</span></span>](security-overview-integration-services.md)  
  
  
