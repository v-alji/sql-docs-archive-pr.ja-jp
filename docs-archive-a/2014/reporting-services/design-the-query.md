---
title: クエリのデザイン |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b56d99ec11b50ce53ef223a01eb5fc2766238ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719677"
---
# <a name="design-the-query"></a><span data-ttu-id="c443c-102">クエリのデザイン</span><span class="sxs-lookup"><span data-stu-id="c443c-102">Design the Query</span></span>
  <span data-ttu-id="c443c-103">レポート ウィザードのこのページを使用すると、手動での入力、クエリ ビルダーでの対話的な操作、他のレポートからのインポートのいずれかの手段でクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c443c-103">Use this page of the Report Wizard to create a query by typing the query manually, by using Query Builder to interactively build a query, or by importing a query from another report.</span></span>  
  
 <span data-ttu-id="c443c-104">[データ ソースを選択します] ページ (レポート ウィザードの前のページ) で選択したデータ ソースの種類によって、このページで入力できるクエリが決まります。</span><span class="sxs-lookup"><span data-stu-id="c443c-104">The data source type you chose on the Select the Data Source page, a previous page in the Report Wizard, determines the query you can enter on this page.</span></span> <span data-ttu-id="c443c-105">たとえば、データソースの種類がである場合、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントまたはストアドプロシージャ名を入力できます。</span><span class="sxs-lookup"><span data-stu-id="c443c-105">For example, if the data source type is [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements or stored procedure names.</span></span> <span data-ttu-id="c443c-106">データソースの種類がの場合 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、クエリペインは無効になり、直接クエリを入力することはできません。</span><span class="sxs-lookup"><span data-stu-id="c443c-106">If the data source type is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], the Query pane is disabled and you cannot enter a query directly.</span></span> <span data-ttu-id="c443c-107">クエリ ビルダーでクエリを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c443c-107">You can specify the query by using Query Builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c443c-108">Options</span><span class="sxs-lookup"><span data-stu-id="c443c-108">Options</span></span>  
 <span data-ttu-id="c443c-109">**クエリ文字列**</span><span class="sxs-lookup"><span data-stu-id="c443c-109">**Query string**</span></span>  
 <span data-ttu-id="c443c-110">レポートで使用するデータを取得するためのクエリを入力します。</span><span class="sxs-lookup"><span data-stu-id="c443c-110">Type a query that retrieves the data you want to use in your report.</span></span>  
  
 <span data-ttu-id="c443c-111">**[クエリ ビルダー]**</span><span class="sxs-lookup"><span data-stu-id="c443c-111">**Query Builder**</span></span>  
 <span data-ttu-id="c443c-112">**[クエリ ビルダー]** をクリックすると、データ ソース用のクエリ デザイナーが開きます。他のレポートからクエリをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c443c-112">Click **Query Builder** to open a query designer for the data source, or to import a query from another report.</span></span>  
  
 <span data-ttu-id="c443c-113">クエリ デザイナーの詳細については、「 [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c443c-113">For more information about query designers, see [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c443c-114">例</span><span class="sxs-lookup"><span data-stu-id="c443c-114">Example</span></span>  
 <span data-ttu-id="c443c-115">**Microsoft SQL Server**データソースの種類の場合、次のクエリでは、データベーステーブルから姓の一覧を取得し [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `Person` ます。</span><span class="sxs-lookup"><span data-stu-id="c443c-115">For the data source type **Microsoft SQL Server**, the following query retrieves a list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Person` table.</span></span>  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 <span data-ttu-id="c443c-116">データソースの種類**Microsoft SQL Server**の場合、次のクエリでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `uspGetEmployeeManagers` 識別番号が1の従業員のストアドプロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="c443c-116">For the data source type **Microsoft SQL Server**, the following query runs the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` for the employee with identification number 1:</span></span>  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a><span data-ttu-id="c443c-117">参照</span><span class="sxs-lookup"><span data-stu-id="c443c-117">See Also</span></span>  
 <span data-ttu-id="c443c-118">[レポートウィザードのヘルプ](../../2014/reporting-services/report-wizard-help.md) </span><span class="sxs-lookup"><span data-stu-id="c443c-118">[Report Wizard Help](../../2014/reporting-services/report-wizard-help.md) </span></span>  
 <span data-ttu-id="c443c-119">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c443c-119">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c443c-120">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="c443c-120">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
