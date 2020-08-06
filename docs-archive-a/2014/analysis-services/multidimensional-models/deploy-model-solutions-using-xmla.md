---
title: XMLA を使用してモデルソリューションを配置する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b78490c5ab6ad3ba5e52bb82d4be254e3f5f102b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741405"
---
# <a name="deploy-model-solutions-using-xmla"></a><span data-ttu-id="3c06f-102">XMLA を使用したモデル ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="3c06f-102">Deploy Model Solutions Using XMLA</span></span>
  <span data-ttu-id="3c06f-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[データベースをスクリプト化]** コマンドの **[CREATE]** オプションを使用すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体またはデータベースを構成するいずれかのオブジェクトの XML スクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3c06f-103">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the **CREATE To** option of the **Script Database As** command creates an XML script of an entire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or one of its constituent objects.</span></span> <span data-ttu-id="3c06f-104">作成したスクリプトは、別のコンピューターで実行し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのスキーマ (メタデータ) を再作成できます。</span><span class="sxs-lookup"><span data-stu-id="3c06f-104">The resulting script can then be run on another computer to recreate the schema (metadata) of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3c06f-105">このスクリプトによって、データベース全体が生成されます。スクリプトを使用するときに、既に配置済みのオブジェクトを増分更新するメカニズムはありません。</span><span class="sxs-lookup"><span data-stu-id="3c06f-105">The script generates the entire database, and there is no mechanism for incrementally updating already deployed objects when using the script.</span></span> <span data-ttu-id="3c06f-106">スクリプトを実行してデータベースを配置したら、新たに作成されたデータベースを処理して、ユーザーが参照できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c06f-106">After running the script and deploying the database, the newly created database must be processed before users can browse it.</span></span>  
  
 <span data-ttu-id="3c06f-107">**[データベースをスクリプト化]** コマンドの詳細については、「 [Analysis Services データベースのドキュメントとスクリプトの作成](document-and-script-an-analysis-services-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c06f-107">For more information about the **Script Database As** command, see [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md).</span></span>  
  
## <a name="modifying-object-properties-in-the-xml-script"></a><span data-ttu-id="3c06f-108">XML スクリプトのオブジェクト プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="3c06f-108">Modifying Object Properties in the XML Script</span></span>  
 <span data-ttu-id="3c06f-109">**[データベースをスクリプト化]** コマンドを使用するとき、データベース オブジェクトの特定のプロパティ (データベース名、データ ソース接続文字列、セキュリティ設定など) を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c06f-109">When using the **Script Database As** command, you cannot modify specific properties (such as the database name, data source connection strings, and security settings) of the database objects.</span></span> <span data-ttu-id="3c06f-110">これらのプロパティは、スクリプトの生成後にスクリプト内で手動で変更するか、スクリプトの実行後に配置済みのデータベースで変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c06f-110">These properties must either be manually modified in the script after the script has been generated or modified in the deployed database after running the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c06f-111">XML スクリプトには、データ ソースへの接続文字列内または権限借用の目的で指定されたパスワードは含まれません。</span><span class="sxs-lookup"><span data-stu-id="3c06f-111">The XML script will not contain the password if this is specified in either the connection string for a data source or for impersonation purposes.</span></span> <span data-ttu-id="3c06f-112">このシナリオの処理ではパスワードが必要であるため、実行前に XML スクリプトに手動でパスワードを追加するか、XML スクリプト実行後にパスワードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c06f-112">Since the password is required for processing purposes in this scenario, you will either need to add this manually to the XML script before it executes or add it after the XML script executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c06f-113">参照</span><span class="sxs-lookup"><span data-stu-id="3c06f-113">See Also</span></span>  
 <span data-ttu-id="3c06f-114">[配置ウィザードを使用したモデルソリューションの配置](deploy-model-solutions-using-the-deployment-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="3c06f-114">[Deploy Model Solutions Using the Deployment Wizard](deploy-model-solutions-using-the-deployment-wizard.md) </span></span>  
 [<span data-ttu-id="3c06f-115">Analysis Services データベースの同期</span><span class="sxs-lookup"><span data-stu-id="3c06f-115">Synchronize Analysis Services Databases</span></span>](synchronize-analysis-services-databases.md)  
  
  
