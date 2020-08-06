---
title: プロジェクトが配置された後にパラメーター値を設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 39572594e429b61de0641c6e6929e84105138f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742393"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a><span data-ttu-id="447f9-102">プロジェクトを配置した後にパラメーターの値を設定する</span><span class="sxs-lookup"><span data-stu-id="447f9-102">Set Parameter Values After the Project Is Deployed</span></span>
  <span data-ttu-id="447f9-103">配置ウィザードを使用すると、プロジェクトをカタログに配置するときにサーバーの既定のパラメーター値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="447f9-103">The Deployment Wizard allows you to set server default parameter values when you deploy your project to the catalog.</span></span> <span data-ttu-id="447f9-104">プロジェクトをカタログに配置した後、SQL Server Management Studio (SSMS) オブジェクト エクスプローラーまたは Transact-SQL を使用して、サーバーの既定値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="447f9-104">After your project is in the catalog, you can use SQL Server Management Studio (SSMS) Object Explorer or Transact-SQL to set server default values.</span></span>  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a><span data-ttu-id="447f9-105">SSMS オブジェクト エクスプ ローラーを使用してサーバーの既定値を設定するには</span><span class="sxs-lookup"><span data-stu-id="447f9-105">To set server defaults with SSMS Object Explorer:</span></span>  
  
1.  <span data-ttu-id="447f9-106">**[Integration Services]** ノードでオブジェクトを選択して右クリックします。</span><span class="sxs-lookup"><span data-stu-id="447f9-106">Select and right-click the project under the **Integration Services** node.</span></span>  
  
2.  <span data-ttu-id="447f9-107">**[プロパティ]** をクリックして、 **[プロジェクトのプロパティ]** ダイアログ ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="447f9-107">Click **Properties** to open the **Project Properties** dialog window.</span></span>  
  
3.  <span data-ttu-id="447f9-108">**[ページの選択]** の **[パラメーター]** をクリックして、パラメーター ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="447f9-108">Open the parameters page by clicking **Parameters** under **Select a page**.</span></span>  
  
4.  <span data-ttu-id="447f9-109">**[パラメーター]** の一覧で目的のパラメーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="447f9-109">Select the desired parameter in the **Parameters** list.</span></span> <span data-ttu-id="447f9-110">注: **[コンテナー]** 列を使用すると、プロジェクト パラメーターとパッケージパラメーターを区別できます。</span><span class="sxs-lookup"><span data-stu-id="447f9-110">Note: The **Container** column helps distinguish project parameters from package parameters.</span></span>  
  
5.  <span data-ttu-id="447f9-111">**[値]** 列で、目的のサーバーの既定のパラメーター値を指定します。</span><span class="sxs-lookup"><span data-stu-id="447f9-111">In the **Value** column, specify the desired server default parameter value.</span></span>  
  
 <span data-ttu-id="447f9-112">Transact-SQL を使用してサーバーの既定値を設定するには、[catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="447f9-112">To set server defaults with Transact-SQL, use the [catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) stored procedure.</span></span> <span data-ttu-id="447f9-113">現在のサーバーの既定値を表示するには、[catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) ビューをクエリします。</span><span class="sxs-lookup"><span data-stu-id="447f9-113">To view current server defaults, query the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span> <span data-ttu-id="447f9-114">サーバーの既定値をクリアするには、[catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="447f9-114">To clear a server default value, use the [catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447f9-115">参照</span><span class="sxs-lookup"><span data-stu-id="447f9-115">See Also</span></span>  
 [<span data-ttu-id="447f9-116">SSIS&#41; パラメーターの Integration Services &#40;</span><span class="sxs-lookup"><span data-stu-id="447f9-116">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
