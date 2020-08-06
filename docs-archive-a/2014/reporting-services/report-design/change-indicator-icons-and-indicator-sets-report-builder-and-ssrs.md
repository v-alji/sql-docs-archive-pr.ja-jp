---
title: インジケーター アイコンとインジケーター セットの変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 398d21319ab6da22f2b10c3607baf8f110d6e65b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737945"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a><span data-ttu-id="08d7d-102">インジケーター アイコンとインジケーター セットの変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="08d7d-102">Change Indicator Icons and Indicator Sets (Report Builder and SSRS)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="08d7d-103">には、あらかじめ構成済みのインジケーター セットが用意されていますが、これらが常にデータを効果的に表したり、配信されたレポートで正しく機能するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="08d7d-103">provides preconfigured indicators sets, which might not always depict your data effectively and work well in the delivered report.</span></span> <span data-ttu-id="08d7d-104">このトピックでは、インジケーター アイコンの外観を変更する手順と、インジケーター セットを変更して別のインジケーター アイコンを含めたり、インジケーター アイコンの数を増減したりする手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-104">This topic provides procedures to change the appearance of indicator icons and change the indicator sets to include different, more, or fewer indicator icons.</span></span>  
  
 <span data-ttu-id="08d7d-105">色などのオプションは、式を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-105">Options such as colors can be set by using expressions.</span></span> <span data-ttu-id="08d7d-106">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d7d-106">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-color-of-an-indicator-icon"></a><span data-ttu-id="08d7d-107">インジケーター アイコンの色を変更するには</span><span class="sxs-lookup"><span data-stu-id="08d7d-107">To change the color of an indicator icon</span></span>  
  
1.  <span data-ttu-id="08d7d-108">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-108">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="08d7d-109">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-109">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="08d7d-110">変更するアイコンの横にある **[色]** 列の下矢印をクリックして、使用する色、 **[色なし]** 、または **[その他の色]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-110">Click the down arrow in the **Color** column next to the icon that you want to change and click the color to use, **No Color**, or **More colors**.</span></span>  
  
     <span data-ttu-id="08d7d-111">必要に応じて、 **式** ( *[fx]* ) ボタンをクリックし、 **[色]** オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-111">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Color** option.</span></span>  
  
     <span data-ttu-id="08d7d-112">**[その他の色]** をクリックした場合は、 **[色の選択]** ダイアログ ボックスが表示され、さまざまな色から選択できます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-112">If you clicked **More Colors**, the **Select Color** dialog box opens, where you can choose from a wide array of colors.</span></span> <span data-ttu-id="08d7d-113">各オプションの詳細については、「[[色の選択] ダイアログ ボックス &#40;レポート ビルダーおよび SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08d7d-113">For more information about its options, see [Select Color Dialog Box &#40;Report Builder and SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="08d7d-114">**[OK]** をクリックして、 **[色の選択]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-114">Click **OK** to close the **Select Color** dialog box.</span></span>  
  
4.  <span data-ttu-id="08d7d-115">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-115">Click **OK**.</span></span>  
  
### <a name="to-change-the-icon"></a><span data-ttu-id="08d7d-116">アイコンを変更するには</span><span class="sxs-lookup"><span data-stu-id="08d7d-116">To change the icon</span></span>  
  
1.  <span data-ttu-id="08d7d-117">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-117">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="08d7d-118">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-118">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="08d7d-119">変更するアイコンの横にある下矢印をクリックして、別のアイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-119">Click the down arrow next to the icon that you want to change and select a different icon.</span></span>  
  
     <span data-ttu-id="08d7d-120">必要に応じて、 **式** ( *[fx]* ) ボタンをクリックし、 **[アイコン]** オプションの値を設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-120">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the value of the **Icon** option.</span></span>  
  
4.  <span data-ttu-id="08d7d-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-121">Click **OK**.</span></span>  
  
### <a name="to-use-a-custom-image-as-an-indicator-icon"></a><span data-ttu-id="08d7d-122">カスタム イメージをインジケーター アイコンとして使用するには</span><span class="sxs-lookup"><span data-stu-id="08d7d-122">To use a custom image as an indicator icon</span></span>  
  
1.  <span data-ttu-id="08d7d-123">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-123">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="08d7d-124">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-124">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="08d7d-125">変更するアイコンの横にある下矢印をクリックして、 **[画像]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-125">Click the down arrow next to the icon that you wan to change and select **Image**.</span></span>  
  
4.  <span data-ttu-id="08d7d-126">**[画像ソースの選択]** の一覧で、 **[外部]** 、 **[埋め込み]** 、または **[データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-126">In the **Select the image source** list, click **External**, **Embedded**, or **Database**.</span></span>  
  
5.  <span data-ttu-id="08d7d-127">画像のソースに応じて、以下のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="08d7d-127">Depending on the source of the image, do the one of the following:</span></span>  
  
    -   <span data-ttu-id="08d7d-128">レポートの外部に保存されている画像を使用するには、 **[参照]** をクリックして画像を見つけます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-128">To use an image that is stored externally to the report, click **Browse** and locate the image.</span></span> <span data-ttu-id="08d7d-129">レポートには、画像への参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-129">The report will include a reference to the image.</span></span>  
  
    -   <span data-ttu-id="08d7d-130">レポートに埋め込まれている画像を使用するには、 **[インポート]** をクリックして画像を見つけます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-130">To use an image that is embedded in the report, click **Import** and locate the image.</span></span> <span data-ttu-id="08d7d-131">画像はレポート定義に追加され、定義と共に保存されます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-131">The image will be added to the report definition and saved with it.</span></span>  
  
    -   <span data-ttu-id="08d7d-132">データベースにある画像を使用するには、 **[次のフィールドを使用]** の一覧から</span><span class="sxs-lookup"><span data-stu-id="08d7d-132">To use an image that is in a database, in the **Use this field** list.</span></span> <span data-ttu-id="08d7d-133">フィールドを選択し、 **[次の MIME の種類を使用]** の一覧から画像の MIME の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-133">select the field from the list and then in the **Use this MIME type** list, select the MIME type of the image.</span></span>  
  
6.  <span data-ttu-id="08d7d-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-134">Click **OK**.</span></span>  
  
### <a name="to-add-an-icon-to-the-indicator-set"></a><span data-ttu-id="08d7d-135">インジケーター セットにアイコンを追加するには</span><span class="sxs-lookup"><span data-stu-id="08d7d-135">To add an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="08d7d-136">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-136">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="08d7d-137">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-137">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="08d7d-138">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-138">Click **Add**.</span></span> <span data-ttu-id="08d7d-139">既定のアイコンと **[色なし]** オプションを使用して、インジケーターが追加されます。</span><span class="sxs-lookup"><span data-stu-id="08d7d-139">An indicator is added, using the default icon and the **No Color** option.</span></span>  
  
     <span data-ttu-id="08d7d-140">指定したアイコンと色を使用するようにインジケーターを構成します。</span><span class="sxs-lookup"><span data-stu-id="08d7d-140">Configure the indictor to use the icon and color you want.</span></span> <span data-ttu-id="08d7d-141">手順については、このトピックの前半で説明しています。</span><span class="sxs-lookup"><span data-stu-id="08d7d-141">Procedures earlier in this topic describe the steps to do this.</span></span>  
  
4.  <span data-ttu-id="08d7d-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-142">Click **OK**.</span></span>  
  
### <a name="to-delete-an-icon-to-the-indicator-set"></a><span data-ttu-id="08d7d-143">インジケーター セットからアイコンを削除するには</span><span class="sxs-lookup"><span data-stu-id="08d7d-143">To delete an icon to the indicator set</span></span>  
  
1.  <span data-ttu-id="08d7d-144">変更するインジケーターを右クリックし、 **[インジケーターのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-144">Right-click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="08d7d-145">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-145">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="08d7d-146">削除するアイコンを選択し、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-146">Select the icon to delete, and click **Delete**.</span></span>  
  
4.  <span data-ttu-id="08d7d-147">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08d7d-147">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d7d-148">参照</span><span class="sxs-lookup"><span data-stu-id="08d7d-148">See Also</span></span>  
 [<span data-ttu-id="08d7d-149">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="08d7d-149">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
