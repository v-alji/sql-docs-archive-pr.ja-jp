---
title: プロパティ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a59d3448-8619-4044-923b-8effba926dfa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d8c77ffbe8e185e15b716819498fe48295348e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712429"
---
# <a name="properties-ssas-tabular"></a><span data-ttu-id="87884-102">プロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="87884-102">Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="87884-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の表形式モデル プロジェクトには、プロジェクト、モデル、レポート、および配置の方法を定義するさまざまなプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="87884-103">Tabular model projects in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] have various properties that define behaviors for the project, model, reporting, and deployment.</span></span> <span data-ttu-id="87884-104">プロパティ設定は、Model.bim ファイルに XML 形式で保存されます。ただし、ここで説明するすべてのプロパティは、 **の** [プロパティ] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]ウィンドウで構成できます。</span><span class="sxs-lookup"><span data-stu-id="87884-104">Property settings are stored in XML format in the Model.bim file, however, all of the properties described in this section can be configured in the **Properties** windows in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="87884-105">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="87884-105">Related Tasks</span></span>  
  
|<span data-ttu-id="87884-106">トピック</span><span class="sxs-lookup"><span data-stu-id="87884-106">Topic</span></span>|<span data-ttu-id="87884-107">説明</span><span class="sxs-lookup"><span data-stu-id="87884-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="87884-108">Power View レポート プロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="87884-108">Power View Reporting Properties &#40;SSAS Tabular&#41;</span></span>](power-view-reporting-properties-ssas-tabular.md)|<span data-ttu-id="87884-109">このセクションのトピックでは、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]に接続して参照される表形式モデルとその構成オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87884-109">Topics in this section provide descriptions and configuration options for tabular models that will be connected to and browsed from [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>|  
|[<span data-ttu-id="87884-110">プロジェクトのプロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="87884-110">Project Properties &#40;SSAS Tabular&#41;</span></span>](project-properties-ssas-tabular.md)|<span data-ttu-id="87884-111">プロジェクトのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87884-111">Provides descriptions for project properties.</span></span> <span data-ttu-id="87884-112">プロジェクトのプロパティには、プロジェクト ファイルおよび配置オプションの設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="87884-112">Project properties include project file and deployment options settings.</span></span>|  
|[<span data-ttu-id="87884-113">モデルのプロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="87884-113">Model Properties &#40;SSAS Tabular&#41;</span></span>](model-properties-ssas-tabular.md)|<span data-ttu-id="87884-114">モデルのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87884-114">Provides descriptions for model properties.</span></span> <span data-ttu-id="87884-115">モデル プロパティは、モデルの作成時に、モデル プロジェクトのビルド アクション、バックアップ、およびワークスペース データベースに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="87884-115">Model properties affect the model project's build actions, backup, and workspace database during model authoring.</span></span>|  
|[<span data-ttu-id="87884-116">テーブルのプロパティ &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="87884-116">Table Properties &#40;SSAS Tabular&#41;</span></span>](table-properties-ssas-tabular.md)|<span data-ttu-id="87884-117">基本的なテーブルのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87884-117">Provides descriptions for basic table properties.</span></span> <span data-ttu-id="87884-118">ここで説明するテーブルのプロパティは、ソースの列が表示されて、列の選択とフィルター処理を行うことができる [テーブルのプロパティの編集] ダイアログ ボックスのプロパティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="87884-118">Table properties described here are different from those in the Edit Table Properties dialog box, which display and allow selection and filtering of columns from the source,</span></span>|  
|[<span data-ttu-id="87884-119">列のプロパティ &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="87884-119">Column Properties &#40;SSAS Tabular&#41;</span></span>](column-properties-ssas-tabular.md)|<span data-ttu-id="87884-120">列のプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87884-120">Provides descriptions for column properties.</span></span> <span data-ttu-id="87884-121">列のプロパティは、列のデータ型、形式、および非表示設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="87884-121">Column properties define a column's data type, format, and hiding settings.</span></span>|  
|[<span data-ttu-id="87884-122">既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="87884-122">Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;</span></span>](configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)|<span data-ttu-id="87884-123">既定のモデリングおよび配置のプロパティについての説明と構成手順が記載されています。</span><span class="sxs-lookup"><span data-stu-id="87884-123">Provides descriptions and configuration steps for default modeling and deployment properties.</span></span> <span data-ttu-id="87884-124">既定のプロパティは、新しい表形式モデル プロジェクトに適用されます。</span><span class="sxs-lookup"><span data-stu-id="87884-124">Default properties apply to new tabular model projects.</span></span> <span data-ttu-id="87884-125">プロジェクトの作成後も、要件に応じて、特定のモデル プロジェクトのこれらのプロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="87884-125">After a project is created, these properties can be changed for a particular model project depending on your requirements.</span></span>|  
  
  
