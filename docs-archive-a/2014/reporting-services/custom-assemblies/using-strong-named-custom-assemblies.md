---
title: 複雑な名前を持つカスタム アセンブリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e685ecda39e0487eb4b469920820fa6e4a10daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631668"
---
# <a name="using-strong-named-custom-assemblies"></a><span data-ttu-id="cb8cd-102">複雑な名前を持つカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="cb8cd-102">Using Strong-Named Custom Assemblies</span></span>
  <span data-ttu-id="cb8cd-103">複雑な名前はアセンブリを識別します。この名前には、アセンブリのマニフェストに格納されたアセンブリのテキスト名、4 つの部分から成るバージョン番号、カルチャ情報 (指定されている場合)、公開キー、およびデジタル署名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-103">A strong name identifies an assembly and includes the assembly's text name, four-part version number, culture information (if provided), a public key, and a digital signature stored in the assembly's manifest.</span></span> <span data-ttu-id="cb8cd-104">複雑な名前は、共通言語ランタイム (CLR) にアセンブリを一意に識別し、バイナリの整合性を確保します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-104">A strong name uniquely identifies an assembly to the common language runtime (CLR) and ensures binary integrity.</span></span>  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a><span data-ttu-id="cb8cd-105">AllowPartiallyTrustedCallersAttribute の使用</span><span class="sxs-lookup"><span data-stu-id="cb8cd-105">Using AllowPartiallyTrustedCallersAttribute</span></span>  
 <span data-ttu-id="cb8cd-106">複雑な名前を持つアセンブリをレポートと一緒に使用するには、アセンブリの **AllowPartiallyTrustedCallers** 属性を使用する部分的に信頼されるコードが複雑な名前を持つアセンブリを呼び出すことを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-106">To use strong-named assemblies with reports, you must allow your strong-named assembly to be called by partially trusted code using the assembly's **AllowPartiallyTrustedCallers** attribute.</span></span> <span data-ttu-id="cb8cd-107">**AllowPartiallyTrustedCallersAttribute** を使用すると、レポート デザイナーまたはレポート サーバーが複雑な名前を持つアセンブリをレポート式で呼び出すことを許可できます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-107">You can use **AllowPartiallyTrustedCallersAttribute** to allow strong-named assemblies to be called by Report Designer or the report server in report expressions.</span></span> <span data-ttu-id="cb8cd-108">部分的に信頼されるコードが複雑な名前を持つアセンブリを呼び出すことを許可するには、アセンブリ属性ファイルに次のアセンブリ レベル属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-108">To allow partially trusted code to call strong-named assemblies, add the following assembly-level attribute to your assembly attribute file.</span></span>  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 <span data-ttu-id="cb8cd-109">**AllowPartiallyTrustedCallersAttribute** は、アセンブリ レベルで複雑な名前を持つアセンブリによって適用された場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-109">**AllowPartiallyTrustedCallersAttribute** is effective only when applied by a strong-named assembly at the assembly level.</span></span> <span data-ttu-id="cb8cd-110">アセンブリレベルで属性を適用する方法の詳細については、SDK ドキュメントの「属性の適用」を参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-110">For more information about applying attributes at the assembly level, see "Applying Attributes" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cb8cd-111">**AllowPartiallyTrustedCallersAttribute** が存在する場合は、既定の **FullTrustLinkDemand** セキュリティ チェックが行われないため、部分的に信頼される他のすべてのアセンブリからそのアセンブリを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-111">When **AllowPartiallyTrustedCallersAttribute** is present, the default **FullTrustLinkDemand** security checks are prevented, making the assembly callable from any other partially trusted assembly.</span></span> <span data-ttu-id="cb8cd-112">すべてのセキュリティ チェックは、クラス レベルやメソッド レベルの宣言セキュリティ属性を含め、明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb8cd-112">All security checks, including class-level or method-level declarative security attributes, must be explicitly stated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8cd-113">参照</span><span class="sxs-lookup"><span data-stu-id="cb8cd-113">See Also</span></span>  
 [<span data-ttu-id="cb8cd-114">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="cb8cd-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
