---
title: レポート定義スキーマのバージョンを確認する (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 413a270a3722ddda1f418c748fa5b7fba50dfeea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716077"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a><span data-ttu-id="4aa3c-102">レポート定義スキーマのバージョンを確認する (SSRS)</span><span class="sxs-lookup"><span data-stu-id="4aa3c-102">Find the Report Definition Schema Version (SSRS)</span></span>
  <span data-ttu-id="4aa3c-103">レポート定義ファイルでは、rdl ファイルの検証に使用されるレポート定義スキーマのバージョンに対応して、RDL 名前空間が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-103">A report definition file specifies the RDL namespace for the version of the report definition schema that is used to validate the rdl file.</span></span> <span data-ttu-id="4aa3c-104">以前の名前空間に対応するレポートが作成済みの場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のレポート デザイナーやレポート ビルダーなどのレポート作成環境で .rdl ファイルを開くと、バックアップ ファイルが自動的に作成され、レポートが現在の名前空間にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-104">When you open an .rdl file in a report authoring environment such as Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or Report Builder, if the report was created for a previous namespace, a backup file is automatically created, and the report is upgraded to the current namespace.</span></span> <span data-ttu-id="4aa3c-105">アップグレードされたレポート定義を保存すると、変換された .rdl ファイルが保存されることになります。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-105">If you save the upgraded report definition, you have saved the converted .rdl file.</span></span> <span data-ttu-id="4aa3c-106">これは、レポート定義をアップグレードする唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-106">This is the only way to upgrade a report definition.</span></span> <span data-ttu-id="4aa3c-107">レポート定義そのものはレポート サーバーでアップグレードされません。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-107">The report definition itself is not upgraded on a report server.</span></span> <span data-ttu-id="4aa3c-108">コンパイル済みレポートが、レポート サーバーで自動的にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-108">The compiled report is upgraded on a report server.</span></span> <span data-ttu-id="4aa3c-109">詳細については、「 [Upgrade Reports](../install-windows/upgrade-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-109">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a><span data-ttu-id="4aa3c-110">レポートの RDL スキーマのバージョンを確認する方法</span><span class="sxs-lookup"><span data-stu-id="4aa3c-110">How to: Identify the RDL Schema Version of a Report</span></span>  
  
1.  <span data-ttu-id="4aa3c-111">メモ帳や、XML を表示できる XML Notepad 2007 などのアプリケーションでレポートの .rdl ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-111">Open the report .rdl file in an application such as Notepad or XML Notepad 2007 in which you can view the xml.</span></span>  
  
     <span data-ttu-id="4aa3c-112">スキーマ名前空間は XML の Report 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-112">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="4aa3c-113">たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-113">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="4aa3c-114">レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`という URL で指定されています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-114">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`.</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a><span data-ttu-id="4aa3c-115">レポート デザイナーの RDL スキーマのバージョンを確認する方法</span><span class="sxs-lookup"><span data-stu-id="4aa3c-115">How to: Identify the RDL Schema Version of Report Designer</span></span>  
  
1.  <span data-ttu-id="4aa3c-116">新しいプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-116">Open a new project.</span></span> <span data-ttu-id="4aa3c-117">選択したプロジェクトのバージョンにより、RDL スキーマのバージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-117">The version of the project that you choose determines the version of the RDL schema.</span></span> <span data-ttu-id="4aa3c-118">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、複数のスキーマ バージョンがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-118">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], more than one schema version is supported.</span></span> <span data-ttu-id="4aa3c-119">詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-119">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="4aa3c-120">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-120">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="4aa3c-121">**[新しい項目の追加]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-121">The **Add New Item** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4aa3c-122">**[テンプレート]** ペインで **[レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-122">In the **Templates** pane, click **Report**.</span></span>  
  
4.  <span data-ttu-id="4aa3c-123">**[名前]** にレポートの名前を入力するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-123">In **Name**, type a report name or accept the default.</span></span>  
  
5.  <span data-ttu-id="4aa3c-124">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-124">Click **Add**.</span></span> <span data-ttu-id="4aa3c-125">レポート デザイナーの [デザイン] ビューに新しい空のレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-125">Report Designer opens a new blank report in Design view.</span></span>  
  
6.  <span data-ttu-id="4aa3c-126">**[表示]** メニューの **[コード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-126">On the **View** menu, click **Code**.</span></span> <span data-ttu-id="4aa3c-127">レポート定義が XML ファイルとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-127">The report definition is displayed as an XML file.</span></span>  
  
     <span data-ttu-id="4aa3c-128">スキーマ名前空間は XML の Report 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-128">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="4aa3c-129">たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-129">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="4aa3c-130">レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="4aa3c-130">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a><span data-ttu-id="4aa3c-131">レポート サーバー上で RDL スキーマのバージョンを確認する方法</span><span class="sxs-lookup"><span data-stu-id="4aa3c-131">How to: Identify the RDL Schema Version on the Report Server</span></span>  
  
-   <span data-ttu-id="4aa3c-132">レポート マネージャーで、レポート サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-132">In Report Manager, type the URL for the report server.</span></span> <span data-ttu-id="4aa3c-133">たとえば、次の URL はローカル コンピューターのレポート サーバーを指定しています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-133">For example, the following URL specifies a report server on the local computer:</span></span>  
  
     `http://localhost/reportserver/reportdefinition.xsd`  
  
     <span data-ttu-id="4aa3c-134">.xsd ファイルがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-134">The .xsd file opens in the browser.</span></span>  
  
     <span data-ttu-id="4aa3c-135">スキーマ名前空間は XML の schema 要素で指定されます。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-135">The XML schema element specifies the schema namespace.</span></span> <span data-ttu-id="4aa3c-136">たとえば、次の schema 要素では、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]によって内部的に使用される targetNamespace 参照、スキーマ自体 (xsd) の xsd 参照、およびレポート定義参照の 3 つの名前空間が指定されています。</span><span class="sxs-lookup"><span data-stu-id="4aa3c-136">For example, the following schema element specifies three namespaces: the targetNamespace reference that is used internally by [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the xsd reference for the schema itself (xsd), and the report definition reference.</span></span>  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     <span data-ttu-id="4aa3c-137">レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="4aa3c-137">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa3c-138">参照</span><span class="sxs-lookup"><span data-stu-id="4aa3c-138">See Also</span></span>  
 <span data-ttu-id="4aa3c-139">[レポートのアップグレード](../install-windows/upgrade-reports.md) </span><span class="sxs-lookup"><span data-stu-id="4aa3c-139">[Upgrade Reports](../install-windows/upgrade-reports.md) </span></span>  
 [<span data-ttu-id="4aa3c-140">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4aa3c-140">Report Definition Language &#40;SSRS&#41;</span></span>](report-definition-language-ssrs.md)  
  
  
