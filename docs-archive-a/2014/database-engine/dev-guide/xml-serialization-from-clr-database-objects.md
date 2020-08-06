---
title: CLR データベースオブジェクトからの XML シリアル化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee93ee4b7bf9cba3f11b329244d4523636cb7704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716654"
---
# <a name="xml-serialization-from-clr-database-objects"></a><span data-ttu-id="5d3e8-102">CLR データベース オブジェクトからの XML シリアル化</span><span class="sxs-lookup"><span data-stu-id="5d3e8-102">XML Serialization from CLR Database Objects</span></span>
  <span data-ttu-id="5d3e8-103">XML シリアル化は、次の 2 つのシナリオで必要になります。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-103">XML serialization is required for two scenarios:</span></span>  
  
-   <span data-ttu-id="5d3e8-104">CLR (共通言語ランタイム) オブジェクトから Web サービスを呼び出す場合。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-104">Invoking Web Services from common language runtime (CLR) objects.</span></span>  
  
-   <span data-ttu-id="5d3e8-105">UDT (ユーザー定義型) を XML に変換する場合。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-105">Converting a user-defined type (UDT) to XML.</span></span>  
  
 <span data-ttu-id="5d3e8-106">`XmlSerializer` クラスを呼び出して XML シリアル化を実行すると、通常、新たにシリアル化アセンブリが生成され、シリアル化の基になるアセンブリを含むプロジェクトにオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-106">Performing XML serialization by invoking the `XmlSerializer` class normally generates an additional serialization assembly that is overloaded into the project with the source assembly.</span></span> <span data-ttu-id="5d3e8-107">ただし、セキュリティ上の理由から、CLR ではこのオーバーロードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-107">However, for security purposes, this overload is disabled in the CLR.</span></span> <span data-ttu-id="5d3e8-108">したがって、web サービスを呼び出したり、内の UDT から XML への変換を実行したりするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必要なシリアル化アセンブリを生成する .NET Framework に用意されている**Sgen.exe**というツールを使用して、アセンブリを手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-108">Therefore, to call a web service or perform conversion from UDT to XML inside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the assembly must be created manually using a tool called **Sgen.exe** provided with the .NET Framework that generates the necessary serialization assemblies.</span></span> <span data-ttu-id="5d3e8-109">`XmlSerializer` を呼び出す場合は、次の手順に従って、シリアル化アセンブリを手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-109">When invoking `XmlSerializer`, the serialization assembly must be created manually by following these steps:</span></span>  
  
1.  <span data-ttu-id="5d3e8-110">.NET Framework SDK に付属している**Sgen.exe**ツールを実行して、ソースアセンブリの XML シリアライザーを含むアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-110">Run the **Sgen.exe** tool that is provided with the .NET Framework SDK to create the assembly containing the XML serializers for the source assembly.</span></span>  
  
2.  <span data-ttu-id="5d3e8-111">`CREATE ASSEMBLY` ステートメントを使用して、生成したアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録します。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-111">Register the generated assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the `CREATE ASSEMBLY` statement.</span></span>  
  
 <span data-ttu-id="5d3e8-112">XML シリアル化の実行時に発生する可能性があるエラーの詳細については、 [「動的に生成されたシリアル化アセンブリを読み込むことができません」](https://support.microsoft.com/kb/913668)という Microsoft サポートの記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-112">For information about errors that you may receive when performing XML serialization, see the following Microsoft Support article: ["Cannot load dynamically generated serialization assembly"](https://support.microsoft.com/kb/913668).</span></span>  
  
 <span data-ttu-id="5d3e8-113">XMLSerializer でサポートされないデータ型については、.NET Framework のドキュメントで、.NET Framework の XML スキーマ バインディング サポートに関する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d3e8-113">For information on data types that are not supported by XMLSerializer, see XML Schema Binding Support in the .NET Framework in the .NET Framework documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3e8-114">参照</span><span class="sxs-lookup"><span data-stu-id="5d3e8-114">See Also</span></span>  
 <span data-ttu-id="5d3e8-115">[CLR データベースオブジェクトからのデータアクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5d3e8-115">[Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="5d3e8-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5d3e8-116">CREATE ASSEMBLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
