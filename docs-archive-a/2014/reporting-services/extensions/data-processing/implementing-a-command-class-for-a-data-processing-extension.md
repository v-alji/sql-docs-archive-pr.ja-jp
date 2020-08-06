---
title: データ処理拡張機能の Command クラスの実装 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f07b9beb798b1cd33ec2fee6af890a09a516b2f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741597"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a><span data-ttu-id="66d24-102">データ処理拡張機能の Command クラスの実装</span><span class="sxs-lookup"><span data-stu-id="66d24-102">Implementing a Command Class for a Data Processing Extension</span></span>
  <span data-ttu-id="66d24-103">**Command** オブジェクトを使用して、要求を作成し、それをデータ ソースに渡します。</span><span class="sxs-lookup"><span data-stu-id="66d24-103">The **Command** object formulates a request and passes it on to the data source.</span></span> <span data-ttu-id="66d24-104">コマンド テキストは、テキスト、XML など多くのさまざまな構文形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="66d24-104">The command text can take many different syntactical forms, including text and XML.</span></span> <span data-ttu-id="66d24-105">結果が返されると、**Command** オブジェクトは、**DataReader** オブジェクトとして結果を返します。</span><span class="sxs-lookup"><span data-stu-id="66d24-105">If results are returned, the **Command** object returns results as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="66d24-106">**Command** クラスを作成するには、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> を実装します。</span><span class="sxs-lookup"><span data-stu-id="66d24-106">To create a **Command** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>.</span></span> <span data-ttu-id="66d24-107">**DataReader** オブジェクトとして結果セットを返すには、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="66d24-107">Implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method to return a result set as a **DataReader** object.</span></span> <span data-ttu-id="66d24-108">**Command** クラスの <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドには、引数として <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 列挙を取得する実装を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d24-108">The <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method of your **Command** class should include an implementation that takes a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> enumeration as an argument.</span></span> <span data-ttu-id="66d24-109">データ処理拡張機能をレポート デザイナーに配置するには、<xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> メソッドで <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> の場合を処理する実装を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d24-109">If you deploy your data processing extension to Report Designer, provide an implementation that handles a <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> case in the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="66d24-110">スキーマだけの実装は、レポート デザイナーにフィールド一覧を提供するために使用します。</span><span class="sxs-lookup"><span data-stu-id="66d24-110">A schema-only implementation is used to supply Report Designer with a fields list.</span></span> <span data-ttu-id="66d24-111"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> メソッドによって返される **DataReader** オブジェクトは、フィールド、つまり、列の型および名前の情報を結果セットに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="66d24-111">The **DataReader** object returned by the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> method needs to contain type and name information for the fields, or columns, in your result set.</span></span>  
  
 <span data-ttu-id="66d24-112">必要に応じて、**Command** クラスは <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装できます。</span><span class="sxs-lookup"><span data-stu-id="66d24-112">Optionally, your **Command** class can implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>.</span></span> <span data-ttu-id="66d24-113">このインターフェイスにより、実装クラスでクエリを分析して、クエリのパラメーターの一覧を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="66d24-113">This interface enables an implementing class to analyze a query and return a list of parameters in the query.</span></span> <span data-ttu-id="66d24-114"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> インターフェイスの機能を使用できるのはレポート デザイナーだけです。</span><span class="sxs-lookup"><span data-stu-id="66d24-114">The functionality of the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> interface is only used in Report Designer.</span></span> <span data-ttu-id="66d24-115"><xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装すると、レポート デザイナーのユーザーがプレビュー モードでレポートを実行するたびに、ユーザーにパラメーターを入力するように要求できます。</span><span class="sxs-lookup"><span data-stu-id="66d24-115">When you implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, you enable users of Report Designer to be prompted for parameters whenever a report is run in preview mode.</span></span> <span data-ttu-id="66d24-116">さらに、**[データセット]** ダイアログの **[パラメーター]** タブでパラメーターを表示できます。</span><span class="sxs-lookup"><span data-stu-id="66d24-116">In addition, you can view the parameters in the **Parameters** tab of the **Data Set** dialog.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66d24-117">カスタム データ処理拡張機能でパラメーターをサポートしない場合は、<xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66d24-117">You should not implement <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> if your custom data processing extension does not support parameters.</span></span>  
  
 <span data-ttu-id="66d24-118">**Command** クラス実装の例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66d24-118">For a sample **Command** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d24-119">参照</span><span class="sxs-lookup"><span data-stu-id="66d24-119">See Also</span></span>  
 <span data-ttu-id="66d24-120">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="66d24-120">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="66d24-121">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="66d24-121">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="66d24-122">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="66d24-122">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
