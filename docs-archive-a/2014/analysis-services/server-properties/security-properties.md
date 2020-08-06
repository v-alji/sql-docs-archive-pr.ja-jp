---
title: セキュリティのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20133554835803908a340c5369eb66e86b119d72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640266"
---
# <a name="security-properties"></a><span data-ttu-id="59b6f-102">セキュリティのプロパティ</span><span class="sxs-lookup"><span data-stu-id="59b6f-102">Security Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="59b6f-103">次の表に示すセキュリティ サーバー プロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="59b6f-103">supports the security server properties listed in the following table.</span></span> <span data-ttu-id="59b6f-104">その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59b6f-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="59b6f-105">**適用対象:** 多次元サーバー モードおよびテーブル サーバー モード</span><span class="sxs-lookup"><span data-stu-id="59b6f-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59b6f-106">Properties</span><span class="sxs-lookup"><span data-stu-id="59b6f-106">Properties</span></span>  
 `RequireClientAuthentication`  
 <span data-ttu-id="59b6f-107">クライアント認証が必要かどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-107">A Boolean property that indicates whether client authentication is required.</span></span>  
  
 <span data-ttu-id="59b6f-108">このプロパティの既定値は True で、クライアント認証が必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="59b6f-108">The default value for this property is True, which indicates that client authentication is required.</span></span>  
  
 `SecurityPackageList`  
 <span data-ttu-id="59b6f-109">サーバーがクライアントの認証に使用する SSPI パッケージのコンマ区切りのリストを格納する文字列プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-109">A string property that contains a comma-separated list of SSPI packages used by server for client authentication.</span></span>  
  
 `DisableClientImpersonation`  
 <span data-ttu-id="59b6f-110">(たとえばストアド プロシージャからの) クライアント権限の借用が無効であるかどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-110">A Boolean property that indicates whether client impersonation (for example, from stored procedures) is disabled.</span></span>  
  
 <span data-ttu-id="59b6f-111">このプロパティの既定値は False で、クライアント権限の借用が有効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="59b6f-111">The default value for this property is False, which indicates that client impersonation is enabled.</span></span>  
  
 `BuiltinAdminsAreServerAdmins`  
 <span data-ttu-id="59b6f-112">ローカル コンピューターの Administrators グループのメンバーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者であるかどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-112">A Boolean property that indicates whether members of the local machine administrators group are [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrators.</span></span>  
  
 `ServiceAccountIsServerAdmin`  
 <span data-ttu-id="59b6f-113">サービス アカウントがサーバー管理者であるかどうかを示すブール型プロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-113">A Boolean property that indicates whether the service account is a server administrator.</span></span>  
  
 <span data-ttu-id="59b6f-114">このプロパティの既定値は True で、サービス アカウントがサーバー管理者であることを示します。</span><span class="sxs-lookup"><span data-stu-id="59b6f-114">The default value for this property is True, which indicates that the service account is a server administrator.</span></span>  
  
 `ErrorMessageMode`  
 <span data-ttu-id="59b6f-115">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="59b6f-115">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="59b6f-116">すべてのクライアント要求に必要な保護レベルを定義する、符号付き 32 ビット整数のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="59b6f-116">A signed 32-bit integer property that defines the required protection level for all client requests.</span></span> <span data-ttu-id="59b6f-117">このプロパティは、次の表に示すいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="59b6f-117">This property has one of the values listed in the following table.</span></span>  
  
|<span data-ttu-id="59b6f-118">値</span><span class="sxs-lookup"><span data-stu-id="59b6f-118">Value</span></span>|<span data-ttu-id="59b6f-119">説明</span><span class="sxs-lookup"><span data-stu-id="59b6f-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="59b6f-120">*0*</span><span class="sxs-lookup"><span data-stu-id="59b6f-120">*0*</span></span>|<span data-ttu-id="59b6f-121">なし。クリア テキストが許可されます。</span><span class="sxs-lookup"><span data-stu-id="59b6f-121">None, clear text allowed.</span></span>|  
|<span data-ttu-id="59b6f-122">*1*</span><span class="sxs-lookup"><span data-stu-id="59b6f-122">*1*</span></span>|<span data-ttu-id="59b6f-123">(既定値) 暗号化が必要。クリア テキストのログは記録されません。</span><span class="sxs-lookup"><span data-stu-id="59b6f-123">(Default) Encryption required, no clear-text logging.</span></span>|  
|<span data-ttu-id="59b6f-124">*2*</span><span class="sxs-lookup"><span data-stu-id="59b6f-124">*2*</span></span>|<span data-ttu-id="59b6f-125">クリア テキストの要求は許可されるが、署名付きのものに限る (暗号化より弱い保護)。</span><span class="sxs-lookup"><span data-stu-id="59b6f-125">Clear-text requests allowed but only with signatures (weaker protection than encryption).</span></span>|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="59b6f-126">詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="59b6f-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b6f-127">参照</span><span class="sxs-lookup"><span data-stu-id="59b6f-127">See Also</span></span>  
 <span data-ttu-id="59b6f-128">[Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="59b6f-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="59b6f-129">Analysis Services インスタンスのサーバー モードの決定</span><span class="sxs-lookup"><span data-stu-id="59b6f-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
