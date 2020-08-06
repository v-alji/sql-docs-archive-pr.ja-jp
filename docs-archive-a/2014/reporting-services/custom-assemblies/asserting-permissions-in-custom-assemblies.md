---
title: カスタム アセンブリでのアクセス許可のアサート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cba3c0b74712b6b4d0f6b5c58925cfd562f0df77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630798"
---
# <a name="asserting-permissions-in-custom-assemblies"></a><span data-ttu-id="4b791-102">カスタム アセンブリでの権限のアサート</span><span class="sxs-lookup"><span data-stu-id="4b791-102">Asserting Permissions in Custom Assemblies</span></span>
  <span data-ttu-id="4b791-103">既定では、カスタム アセンブリ コードは、限定された **Execution** アクセス許可セットに基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="4b791-103">By default, custom assembly code runs with the limited **Execution** permission set.</span></span> <span data-ttu-id="4b791-104">ただし、場合によっては、(ファイルやレジストリなど) セキュリティ システムで保護されたリソースを安全に呼び出すカスタム アセンブリを実装する必要が生じる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4b791-104">In some cases, you may wish to implement a custom assembly that makes secured calls to protected resources within your security system (such as a file or the registry).</span></span> <span data-ttu-id="4b791-105">そのためには、次の操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-105">In order to accomplish this, you must do the following:</span></span>  
  
1.  <span data-ttu-id="4b791-106">セキュリティで保護された呼び出しを行うために、コードに必要な正しい権限を識別します。</span><span class="sxs-lookup"><span data-stu-id="4b791-106">Identify the exact permissions that your code needs in order to make the secured call.</span></span> <span data-ttu-id="4b791-107">このメソッドがライブラリの一部である場合は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 、この情報をメソッドドキュメントに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-107">If this method is part of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] library, this information should be included in the method documentation.</span></span>  
  
2.  <span data-ttu-id="4b791-108">カスタム アセンブリに必要な権限を与えるために、レポート サーバー ポリシーの構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="4b791-108">Modify the report server policy configuration files in order to grant the custom assembly the required permissions.</span></span> <span data-ttu-id="4b791-109">セキュリティ ポリシー構成ファイルの詳細については、「[Reporting Services セキュリティ ポリシー ファイルの使用](../extensions/secure-development/using-reporting-services-security-policy-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b791-109">For more information about the security policy configuration files, see [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).</span></span>  
  
3.  <span data-ttu-id="4b791-110">セキュリティで保護された呼び出しを行うメソッドの一部として、必要な権限をアサートします。</span><span class="sxs-lookup"><span data-stu-id="4b791-110">Assert the required permissions as part of the method in which the secure call is made.</span></span> <span data-ttu-id="4b791-111">レポート サーバーによって呼び出されるカスタム アセンブリ コードは、レポート式のホスト アセンブリの一部であり、既定では **Execution** アクセス許可で実行するため、このアサートが必要です。</span><span class="sxs-lookup"><span data-stu-id="4b791-111">This is required because the custom assembly code that is called by the report server is part of the report expression host assembly, which runs with **Execution** permission by default.</span></span> <span data-ttu-id="4b791-112">**Execution** アクセス許可セットでコードを実行できますが、保護されたリソースを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b791-112">The **Execution** permission set enables code to run, but not to use protected resources.</span></span>  
  
4.  <span data-ttu-id="4b791-113">カスタム アセンブリが厳密な名前で署名されている場合、カスタム アセンブリを **AllowPartiallyTrustedCallersAttribute** でマークします。</span><span class="sxs-lookup"><span data-stu-id="4b791-113">Mark the custom assembly with **AllowPartiallyTrustedCallersAttribute** if it is signed with a strong name.</span></span> <span data-ttu-id="4b791-114">カスタム アセンブリは、レポート式のホスト アセンブリの一部であるレポート式から呼び出され、既定では、**FullTrust** が与えられていない、つまり、"部分的な信頼関係のある" 呼び出し元であるため、このマークが必要です。</span><span class="sxs-lookup"><span data-stu-id="4b791-114">This is required because custom assemblies are called from a report expression that is part of the report expression host assembly, which, by default, is not granted **FullTrust**; thus it is a "partially trusted" caller.</span></span> <span data-ttu-id="4b791-115">詳細については、「[複雑な名前を持つカスタム アセンブリの使用](using-strong-named-custom-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b791-115">For more information, see [Using Strong-Named Custom Assemblies](using-strong-named-custom-assemblies.md).</span></span>  
  
## <a name="implementing-a-secure-call"></a><span data-ttu-id="4b791-116">セキュリティで保護された呼び出しの実装</span><span class="sxs-lookup"><span data-stu-id="4b791-116">Implementing a Secure Call</span></span>  
 <span data-ttu-id="4b791-117">ポリシーの構成ファイルを変更して、アセンブリに特定の権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="4b791-117">You can modify the policy configuration files to grant your assembly specific permissions.</span></span> <span data-ttu-id="4b791-118">たとえば、通貨換算を処理するためにカスタム アセンブリを書き込んだ場合、現在の通貨換算レートをファイルから読み取らなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-118">For example, if you were writing a custom assembly to handle currency conversion, you might need to read the current currency exchange rates from a file.</span></span> <span data-ttu-id="4b791-119">換算レート情報を取得するには、追加セキュリティ アクセス許可 **FileIOPermission** をアセンブリのアクセス許可セットに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-119">To retrieve the rate information, you would need to add an additional security permission, **FileIOPermission**, to your permission set for the assembly.</span></span> <span data-ttu-id="4b791-120">ポリシーの構成ファイルで次の追加エントリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4b791-120">You can make the following additional entry in the policy configuration file:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="4b791-121">次のように、アセンブリの権限セットを参照するコード グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="4b791-121">You then add a code group that references that permission set:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 <span data-ttu-id="4b791-122">コードに適切な権限を取得するためには、カスタム アセンブリ コード内で権限をアサートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-122">In order for your code to acquire the appropriate permission, you must assert the permission within your custom assembly code.</span></span> <span data-ttu-id="4b791-123">たとえば、XML ファイル C:\CurrencyRates.xml の読み取り専用アクセスを追加する場合、次のコードをメソッドに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b791-123">For example, if you want to add read-only access to an XML file, C:\CurrencyRates.xml, you must add the following code to your method:</span></span>  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 <span data-ttu-id="4b791-124">次のように、アサーションをメソッド属性として追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b791-124">You can also add the assertion as a method attribute:</span></span>  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 <span data-ttu-id="4b791-125">詳細については、『.NET Framework 開発者ガイド』の「.NET Framework セキュリティ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b791-125">For more information, see ".NET Framework Security" in the .NET Framework Developer's Guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b791-126">参照</span><span class="sxs-lookup"><span data-stu-id="4b791-126">See Also</span></span>  
 [<span data-ttu-id="4b791-127">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="4b791-127">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
