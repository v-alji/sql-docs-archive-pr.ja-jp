---
title: '[MSSQLSERVER のプロトコルのプロパティ] ダイアログ ボックス ([証明書] タブ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
ms.openlocfilehash: 020d33eba7621f877f8622ca89dbd26a071f16a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737297"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a><span data-ttu-id="51f9b-102">[MSSQLSERVER のプロトコルのプロパティ] ダイアログ ボックス ([証明書] タブ)</span><span class="sxs-lookup"><span data-stu-id="51f9b-102">Protocols for MSSQLSERVER Properties (Certificate Tab)</span></span>
  <span data-ttu-id="51f9b-103">**[MSSQLSERVER のプロトコルのプロパティ]** ダイアログ ボックスの **[証明書]** タブを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の証明書の選択や、証明書のプロパティの表示を行います。</span><span class="sxs-lookup"><span data-stu-id="51f9b-103">Use the **Certificate** tab on the **Protocols for MSSQLSERVER Properties** dialog box to select a certificate for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or to view the properties of a certificate.</span></span> <span data-ttu-id="51f9b-104">証明書を選択するまで、すべてのフィールドは空になっています。</span><span class="sxs-lookup"><span data-stu-id="51f9b-104">All fields are blank until a certificate is selected.</span></span>  
  
 <span data-ttu-id="51f9b-105">証明書は、コンピューター上のユーザーにローカルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="51f9b-105">Certificates are stored locally for the users on the computer.</span></span> <span data-ttu-id="51f9b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用する証明書を読み込むには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスと同じユーザー アカウントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="51f9b-106">To load a certificate for use by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must be running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager under the same user account as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="51f9b-107">ページ ヘッダー</span><span class="sxs-lookup"><span data-stu-id="51f9b-107">Page Header</span></span>  
 <span data-ttu-id="51f9b-108">**表示**</span><span class="sxs-lookup"><span data-stu-id="51f9b-108">**View**</span></span>  
 <span data-ttu-id="51f9b-109">証明書の詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="51f9b-109">Provides access to additional details on the certificate.</span></span> <span data-ttu-id="51f9b-110">**[証明書]** ボックスで証明書を選択するまで使用できません。</span><span class="sxs-lookup"><span data-stu-id="51f9b-110">Not available until a certificate is selected in the **Certificate** box.</span></span> <span data-ttu-id="51f9b-111">証明書の詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51f9b-111">For additional information on certificate details, see your [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
 <span data-ttu-id="51f9b-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="51f9b-112">**Clear**</span></span>  
 <span data-ttu-id="51f9b-113">**[証明書]** ボックスの選択項目を削除します。</span><span class="sxs-lookup"><span data-stu-id="51f9b-113">Removes the selection from the **Certificate** box.</span></span>  
  
 <span data-ttu-id="51f9b-114">**[MSSQLSERVER のプロトコルのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="51f9b-114">**Certificate**</span></span>  
 <span data-ttu-id="51f9b-115">セキュリティ プロバイダーによって判別される証明書の名前です。</span><span class="sxs-lookup"><span data-stu-id="51f9b-115">Name of certificate as determined by security provider.</span></span> <span data-ttu-id="51f9b-116">証明書を選択すると、プロパティのグリッドに詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="51f9b-116">Select a certificate to see the details in the properties grid.</span></span>  
  
## <a name="options"></a><span data-ttu-id="51f9b-117">オプション</span><span class="sxs-lookup"><span data-stu-id="51f9b-117">Options</span></span>  
 <span data-ttu-id="51f9b-118">[有効期限]</span><span class="sxs-lookup"><span data-stu-id="51f9b-118">Expiration Date</span></span>  
 <span data-ttu-id="51f9b-119">証明書の有効期間の最終日付です。</span><span class="sxs-lookup"><span data-stu-id="51f9b-119">The final date for the period in which the certificate is valid.</span></span>  
  
 <span data-ttu-id="51f9b-120">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="51f9b-120">Friendly Name</span></span>  
 <span data-ttu-id="51f9b-121">証明書の発行先の個人または認証局を表す表示名または一般名です。</span><span class="sxs-lookup"><span data-stu-id="51f9b-121">A friendly or common name for the individual or certification authority to whom the certificate is issued.</span></span>  
  
 <span data-ttu-id="51f9b-122">[発行元]</span><span class="sxs-lookup"><span data-stu-id="51f9b-122">Issued By</span></span>  
 <span data-ttu-id="51f9b-123">証明書を発行した証明機関に関する情報。</span><span class="sxs-lookup"><span data-stu-id="51f9b-123">Information regarding the certification authority that issued the certificate.</span></span>  
  
 <span data-ttu-id="51f9b-124">[発行先]</span><span class="sxs-lookup"><span data-stu-id="51f9b-124">Issued To</span></span>  
 <span data-ttu-id="51f9b-125">証明書の受信者に関する情報です。</span><span class="sxs-lookup"><span data-stu-id="51f9b-125">Information regarding the recipient of the certificate.</span></span>  
  
  
