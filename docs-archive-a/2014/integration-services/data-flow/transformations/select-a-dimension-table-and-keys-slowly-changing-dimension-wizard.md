---
title: '[ディメンション テーブルおよびキーの選択] (緩やかに変化するディメンション ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 671c66a8a5d5f1f4f5201fd8c9ecc144540d8b68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743401"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a><span data-ttu-id="7a857-102">[ディメンション テーブルおよびキーの選択] (緩やかに変化するディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="7a857-102">Select a Dimension Table and Keys (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="7a857-103">**[ディメンション テーブルおよびキーの選択]** ページを使用すると、読み込むディメンション テーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7a857-103">Use the **Select a Dimension Table and Keys** page to select a dimension table to load.</span></span> <span data-ttu-id="7a857-104">データ フローの列を、読み込み対象の列にマップします。</span><span class="sxs-lookup"><span data-stu-id="7a857-104">Map columns from the data flow to the columns that will be loaded.</span></span>  
  
 <span data-ttu-id="7a857-105">このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a857-105">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a857-106">オプション</span><span class="sxs-lookup"><span data-stu-id="7a857-106">Options</span></span>  
 <span data-ttu-id="7a857-107">**Connection manager**</span><span class="sxs-lookup"><span data-stu-id="7a857-107">**Connection manager**</span></span>  
 <span data-ttu-id="7a857-108">一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして OLE DB 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7a857-108">Select an existing OLE DB connection manager from the list, or click **New** to create an OLE DB connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a857-109">緩やかに変化するディメンション ウィザードでは、OLE DB 接続マネージャーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a857-109">The Slowly Changing Dimension Wizard only supports OLE DB connection managers, and only supports connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7a857-110">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="7a857-110">**New**</span></span>  
 <span data-ttu-id="7a857-111">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して既存の接続マネージャを選択するか、 **[新規作成]** をクリックして新しい OLE DB 接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7a857-111">Use the **Configure OLE DB Connection Manager** dialog box to select an existing connection manager, or click **New** to create a new OLE DB connection.</span></span>  
  
 <span data-ttu-id="7a857-112">**[テーブルまたはビュー]**</span><span class="sxs-lookup"><span data-stu-id="7a857-112">**Table or View**</span></span>  
 <span data-ttu-id="7a857-113">一覧からテーブルまたはビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a857-113">Select a table or view from the list.</span></span>  
  
 <span data-ttu-id="7a857-114">**[入力列]**</span><span class="sxs-lookup"><span data-stu-id="7a857-114">**Input Columns**</span></span>  
 <span data-ttu-id="7a857-115">マッピングを指定する入力列を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="7a857-115">Select from the list of input columns for which you may specify mapping.</span></span>  
  
 <span data-ttu-id="7a857-116">**[ディメンション列]**</span><span class="sxs-lookup"><span data-stu-id="7a857-116">**Dimension Columns**</span></span>  
 <span data-ttu-id="7a857-117">使用できるすべてのディメンション列を表示します。</span><span class="sxs-lookup"><span data-stu-id="7a857-117">View all available dimension columns.</span></span>  
  
 <span data-ttu-id="7a857-118">**[キーの種類]**</span><span class="sxs-lookup"><span data-stu-id="7a857-118">**Key Type**</span></span>  
 <span data-ttu-id="7a857-119">ビジネス キーとして使用するディメンション列を 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="7a857-119">Select one of the dimension columns to be the business key.</span></span> <span data-ttu-id="7a857-120">ビジネス キーを必ず 1 つ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a857-120">You must have one business key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a857-121">参照</span><span class="sxs-lookup"><span data-stu-id="7a857-121">See Also</span></span>  
 [<span data-ttu-id="7a857-122">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="7a857-122">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
