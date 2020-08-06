---
title: Power View レポートの既定のフィールドセットの構成 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66fbbacd0cc2efd7d379bcc8e68149551476869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712473"
---
# <a name="configure-default-field-set-for-power-view-reports-ssas-tabular"></a><span data-ttu-id="7a5fa-102">Power View レポートの既定のフィールド セットの構成 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="7a5fa-102">Configure Default Field Set for Power View Reports (SSAS Tabular)</span></span>
  <span data-ttu-id="7a5fa-103">既定のフィールド セットは、列とメジャーの定義済みリストであり、レポート フィールド リストでテーブルを選択したときに、自動的に [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート キャンバスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-103">A default field set is a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span> <span data-ttu-id="7a5fa-104">テーブル モデルの作成者が既定のフィールド セットを作成しておけば、レポートの作成者がレポートのためにモデルを使用するときに、余分な手順を省くことができます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-104">Tabular model authors can create a default field set to eliminate redundant steps for report authors who use the model for their reports.</span></span> <span data-ttu-id="7a5fa-105">たとえば、顧客の連絡先情報を参照するほとんどのレポート作成者が、連絡先の名前、通常の電話番号、電子メール アドレス、および会社名を常に確認する必要があることがわかっている場合は、これらの列をあらかじめ選択し、作成者が Customer Contact テーブルをクリックしたときに、これらの列が常にレポート キャンバスに追加されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-105">For example, if you know that most report authors who work with customer contact information always want to see a contact name, a primary phone number, an email address, and a company name, you can pre-select those columns so that they are always added to the report canvas when the author clicks the Customer Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a5fa-106">既定のフィールド セットは、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]でデータ モデルとして使用されるテーブル モデルのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-106">A default field set applies only to a tabular model used as a data model in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="7a5fa-107">既定のフィールド セットは、Excel ピボット レポートではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-107">Default field sets are not supported in Excel pivot reports.</span></span>  
  
## <a name="creating-a-default-field-set"></a><span data-ttu-id="7a5fa-108">既定のフィールド セットの作成</span><span class="sxs-lookup"><span data-stu-id="7a5fa-108">Creating a Default Field Set</span></span>  
 <span data-ttu-id="7a5fa-109">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]で特定のテーブルが選択されたときに、どのフィールドが既定で含まれるかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-109">You can determine which fields, if any, are included by default whenever a specific table is selected in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="7a5fa-110">フィールドが一覧に表示される順序も決定できます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-110">You can also determine the order in which fields appear in the list.</span></span> <span data-ttu-id="7a5fa-111">既定のフィールド セットを指定するには、テーブル モデル プロジェクトにレポート プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-111">To specify a default field set, you set report properties in the tabular model project.</span></span>  
  
#### <a name="to-add-a-default-field-set"></a><span data-ttu-id="7a5fa-112">既定のフィールド セットを追加するには</span><span class="sxs-lookup"><span data-stu-id="7a5fa-112">To add a default field set</span></span>  
  
1.  <span data-ttu-id="7a5fa-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、既定のフィールド セットを構成する対象のテーブル (タブ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the table (tab) for which you are configuring a default field list.</span></span>  
  
2.  <span data-ttu-id="7a5fa-114">**[プロパティ]** ウィンドウの **既定のフィールド セット** プロパティで、 **[クリックして編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-114">In the **Properties** window, in the **Default Field Set** property, click **Click to edit**.</span></span>  
  
3.  <span data-ttu-id="7a5fa-115">[既定のフィールド セット] ダイアログで、フィールドを 1 つ以上選択します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-115">In the Default Field Set dialog, select one or more fields.</span></span> <span data-ttu-id="7a5fa-116">メジャーを含め、テーブル内の任意のフィールドを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-116">You can choose any field in the table, including measures.</span></span> <span data-ttu-id="7a5fa-117">Shift キーを押しながら範囲を選択するか、Ctrl キーを押しながら個別のフィールドを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-117">Hold down the Shift key to select a range, or the Ctrl key to select individual fields.</span></span>  
  
4.  <span data-ttu-id="7a5fa-118">**[追加]** をクリックして、選択したフィールドを既定のフィールド セットに追加します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-118">Click **Add** to add them to the default field set.</span></span>  
  
5.  <span data-ttu-id="7a5fa-119">上矢印ボタンと下矢印ボタンを使用して、フィールド リストに順番を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-119">Use the Up and Down buttons to specify an order to the field list.</span></span> <span data-ttu-id="7a5fa-120">フィールドは、フィールド リストに定義された順番でレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-120">Fields will be added to the report in the order defined for the field set.</span></span>  
  
6.  <span data-ttu-id="7a5fa-121">ブックの他のテーブルについて、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-121">Repeat these steps for other tables in your workbook.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7a5fa-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="7a5fa-122">Next Step</span></span>  
 <span data-ttu-id="7a5fa-123">既定のフィールド セットを作成した後、既定のラベル、既定の画像、既定のグループ動作、または同じ値を含む行を 1 行にグループ化するか個別に表示するかを指定することによって、レポートのデザイン作業にさらに影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-123">After you create a default field set, you can further influence the report design experience by specifying default labels, default images, default group behavior, or whether rows that contain the same value are grouped together in one row or listed individually.</span></span> <span data-ttu-id="7a5fa-124">詳細については、「[Power View レポートのテーブル動作プロパティの構成 (SSAS テーブル)](power-view-configure-table-behavior-properties-for-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a5fa-124">For more information, see [Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;](power-view-configure-table-behavior-properties-for-reports.md).</span></span>  
  
  
