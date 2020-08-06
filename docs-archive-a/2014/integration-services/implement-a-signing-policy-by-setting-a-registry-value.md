---
title: レジストリ値を設定して署名ポリシーを実装する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing policies [Integration Services]
ms.assetid: 64f6966f-2292-401f-acb1-2ccb5aee484a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e844b65df5b45f212554f7583f4e4b327b740e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632580"
---
# <a name="implement-a-signing-policy-by-setting-a-registry-value"></a><span data-ttu-id="b7061-102">レジストリ値を設定して署名ポリシーを実装する</span><span class="sxs-lookup"><span data-stu-id="b7061-102">Implement a Signing Policy by Setting a Registry Value</span></span>
  <span data-ttu-id="b7061-103">オプションのレジストリ値を使用して、署名付きパッケージまたは署名がないパッケージを読み込む際の組織のポリシーを管理できます。</span><span class="sxs-lookup"><span data-stu-id="b7061-103">You can use an optional registry value to manage an organization's policy for loading signed or unsigned packages.</span></span> <span data-ttu-id="b7061-104">このレジストリ キーを使用する場合、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] が実行されるコンピューターおよびポリシーを適用するコンピューターごとにこのレジストリ値を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7061-104">If you use this registry value, you must create this registry value on each computer on which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages will run and on which you want to enforce the policy.</span></span> <span data-ttu-id="b7061-105">レジストリ値が設定されると、パッケージを読み込む前に、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] によって署名が確認されます。</span><span class="sxs-lookup"><span data-stu-id="b7061-105">After the registry value has been set, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] will check or verify the signatures before loading packages.</span></span>  
  
 <span data-ttu-id="b7061-106">このトピックの手順では、オプションの `BlockedSignatureStates` DWORD 値をレジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS に追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7061-106">This procedure in this topic describes how to add the optional `BlockedSignatureStates` DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS registry key.</span></span> <span data-ttu-id="b7061-107">`BlockedSignatureStates` のデータ値は、署名が信頼できない場合、署名が無効な場合、または署名がない場合に、そのパッケージをブロックするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b7061-107">The data value in `BlockedSignatureStates` determines whether a package should be blocked if it has an untrusted signature, has an invalid signature, or is unsigned.</span></span> <span data-ttu-id="b7061-108">パッケージの署名に使用される署名のステータスについて、`BlockedSignatureStates` レジストリ値では以下の定義が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b7061-108">With regard to the status of signatures used to sign packages, the `BlockedSignatureStates` registry value uses the following definitions:</span></span>  
  
-   <span data-ttu-id="b7061-109">*有効な署名* とは、正常に読み取ることができる署名のことです。</span><span class="sxs-lookup"><span data-stu-id="b7061-109">A *valid signature* is one that can be read successfully.</span></span>  
  
-   <span data-ttu-id="b7061-110">*無効な署名* とは、暗号化解除済みのチェックサム (秘密キーによって暗号化されたパッケージ コードの一方向のハッシュ) が、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを読み込むプロセスの一部として計算された暗号化解除済みのチェックサムと一致しない署名のことです。</span><span class="sxs-lookup"><span data-stu-id="b7061-110">An *invalid signature* is one for which the decrypted checksum (the one-way hash of the package code encrypted by a private key) does not match the decrypted checksum that is calculated as part of the process of loading [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
-   <span data-ttu-id="b7061-111">*信頼できる署名* とは、信頼されているルート証明機関により署名されたデジタル証明書を使用して作成される署名のことです。</span><span class="sxs-lookup"><span data-stu-id="b7061-111">A *trusted signature* is one that is created by using a digital certificate signed by a Trusted Root Certification Authority.</span></span> <span data-ttu-id="b7061-112">この設定で、署名者は、ユーザーの信頼できる発行元のリストに含まれている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b7061-112">This setting does not require the signer to be found in the user's list of Trusted Publishers.</span></span>  
  
-   <span data-ttu-id="b7061-113">*信頼できない署名* とは、信頼されているルート証明機関によって発行されたことを確認できない署名、または最新ではない署名のことです。</span><span class="sxs-lookup"><span data-stu-id="b7061-113">An *untrusted signature* is one that cannot be verified as issued by a Trusted Root Certification Authority, or a signature that is not current.</span></span>  
  
 <span data-ttu-id="b7061-114">次の表に、DWORD データの有効な値、およびそれらに関連付けられたポリシーを示します。</span><span class="sxs-lookup"><span data-stu-id="b7061-114">The following table lists the valid values of the DWORD data and their associated policy.</span></span>  
  
|<span data-ttu-id="b7061-115">値</span><span class="sxs-lookup"><span data-stu-id="b7061-115">Value</span></span>|<span data-ttu-id="b7061-116">説明</span><span class="sxs-lookup"><span data-stu-id="b7061-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b7061-117">0</span><span class="sxs-lookup"><span data-stu-id="b7061-117">0</span></span>|<span data-ttu-id="b7061-118">管理制限はありません。</span><span class="sxs-lookup"><span data-stu-id="b7061-118">No administrative restriction.</span></span>|  
|<span data-ttu-id="b7061-119">1</span><span class="sxs-lookup"><span data-stu-id="b7061-119">1</span></span>|<span data-ttu-id="b7061-120">署名が無効なパッケージをブロックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-120">Block invalid signatures.</span></span><br /><br /> <span data-ttu-id="b7061-121">この設定では、署名がないパッケージはブロックしません。</span><span class="sxs-lookup"><span data-stu-id="b7061-121">This setting does not block unsigned packages.</span></span>|  
|<span data-ttu-id="b7061-122">2</span><span class="sxs-lookup"><span data-stu-id="b7061-122">2</span></span>|<span data-ttu-id="b7061-123">署名が無効または信頼できないパッケージをブロックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-123">Block invalid and untrusted signatures.</span></span><br /><br /> <span data-ttu-id="b7061-124">この設定では、署名がないパッケージをブロックしませんが、自己生成された署名をブロックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-124">This setting does not block unsigned packages, but blocks self-generated signatures.</span></span>|  
|<span data-ttu-id="b7061-125">3</span><span class="sxs-lookup"><span data-stu-id="b7061-125">3</span></span>|<span data-ttu-id="b7061-126">署名が無効であるか署名が信頼できないパッケージ、および署名がないパッケージをブロックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-126">Block invalid and untrusted signatures and unsigned packages</span></span><br /><br /> <span data-ttu-id="b7061-127">この設定では、自己生成された署名もブロックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-127">This setting also blocks self-generated signatures.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b7061-128">`BlockedSignatureStates` の推奨設定値は 3 です。</span><span class="sxs-lookup"><span data-stu-id="b7061-128">The recommended setting for `BlockedSignatureStates` is 3.</span></span> <span data-ttu-id="b7061-129">この設定では、署名されていないパッケージまたは無効な署名や信頼できない署名に対する最大の保護が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b7061-129">This setting provides the greatest protection against unsigned packages or signatures that are either not valid or untrusted.</span></span> <span data-ttu-id="b7061-130">ただし、推奨される設定がすべての状況に適しているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b7061-130">However, the recommended setting may not be appropriate in all circumstances.</span></span> <span data-ttu-id="b7061-131">デジタル アセットの署名の詳細については、MSDN ライブラリの「[コード署名の概要](https://go.microsoft.com/fwlink/?LinkId=51414)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7061-131">For more information about signing digital assets, see the topic, "[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)," in the MSDN Library.</span></span>  
  
### <a name="to-implement-a-signing-policy-for-packages"></a><span data-ttu-id="b7061-132">パッケージに対する署名ポリシーを実装するには</span><span class="sxs-lookup"><span data-stu-id="b7061-132">To implement a signing policy for packages</span></span>  
  
1.  <span data-ttu-id="b7061-133">**[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="b7061-134">[実行] ダイアログボックスで、「」と入力し、 `Regedit` [ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-134">In the Run dialog box, type `Regedit`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b7061-135">レジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS を探します。</span><span class="sxs-lookup"><span data-stu-id="b7061-135">Locate the registry key, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS.</span></span>  
  
4.  <span data-ttu-id="b7061-136">**[MSDTS]** を右クリックし、 **[新規]** をポイントして、 **[DWORD 値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-136">Right-click **MSDTS**, point to **New**, and then click **DWORD Value**.</span></span>  
  
5.  <span data-ttu-id="b7061-137">新しい値の名前を「`BlockedSignatureStates`」に更新します。</span><span class="sxs-lookup"><span data-stu-id="b7061-137">Update the name of the new value to `BlockedSignatureStates`.</span></span>  
  
6.  <span data-ttu-id="b7061-138">右クリック `BlockedSignatureStates` して、[**変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-138">Right-click `BlockedSignatureStates` and click **Modify**.</span></span>  
  
7.  <span data-ttu-id="b7061-139">**[DWORD 値の編集]** ダイアログ ボックスで、「0」、「1」、「2」、または「3」のいずれかの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b7061-139">In the **Edit DWORD Value** dialog box, type the value 0, 1, 2, or 3.</span></span>  
  
8.  <span data-ttu-id="b7061-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-140">Click **OK**.</span></span>  
  
9. <span data-ttu-id="b7061-141">**[ファイル]** メニューの **[終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7061-141">On the **File** menu, click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7061-142">参照</span><span class="sxs-lookup"><span data-stu-id="b7061-142">See Also</span></span>  
 <span data-ttu-id="b7061-143">[セキュリティの概要 &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="b7061-143">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="b7061-144">デジタル署名を使用してパッケージのソースを特定する</span><span class="sxs-lookup"><span data-stu-id="b7061-144">Identify the Source of Packages with Digital Signatures</span></span>](security/identify-the-source-of-packages-with-digital-signatures.md)  
  
  
