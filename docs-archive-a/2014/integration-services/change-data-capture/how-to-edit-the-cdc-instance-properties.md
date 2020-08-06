---
title: CDC インスタンスのプロパティを編集する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b02785a32fa1f64d5da0c3202acd7916da1e65ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712289"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a><span data-ttu-id="7d49d-102">CDC インスタンスのプロパティを編集する方法</span><span class="sxs-lookup"><span data-stu-id="7d49d-102">How to Edit the CDC Instance Properties</span></span>
  <span data-ttu-id="7d49d-103">この手順では、CDC デザイナー コンソールを使用して CDC インスタンスの構成プロパティを編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-103">This procedure describes how to use the CDC Designer Console to edit the configuration properties for a CDC instance.</span></span>  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a><span data-ttu-id="7d49d-104">CDC インスタンスの構成プロパティを編集するには</span><span class="sxs-lookup"><span data-stu-id="7d49d-104">To edit the CDC instance configuration properties</span></span>  
  
1.  <span data-ttu-id="7d49d-105">**[スタート]** メニューの **[CDC デザイナー コンソール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d49d-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="7d49d-106">左側のペインで **[Change Data Capture]** を展開し、プロパティを編集するインスタンスが含まれているサービスを展開します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance with the properties that you want to edit.</span></span>  
  
3.  <span data-ttu-id="7d49d-107">プロパティを編集するインスタンスの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-107">Select the name of the instance where you want to edit the properties.</span></span>  
  
4.  <span data-ttu-id="7d49d-108">CDC デザイナー コンソールの右側にある [アクション] ペインで **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d49d-108">From the Actions pane on the right side of the CDC Designer Console, click **Properties**.</span></span>  
  
     <span data-ttu-id="7d49d-109">プロパティを編集するインスタンスを右クリックして **[プロパティ]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7d49d-109">You can also right-click the instance where you want to edit the properties and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="7d49d-110">プロパティ エディターで、次のタブのプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-110">In the Properties editor, edit the properties in the following tabs:</span></span>  
  
    -   <span data-ttu-id="7d49d-111">**[Oracle]** : プロパティ エディターの **[Oracle]** タブを使用して、新しいインスタンス ウィザードの [CDC データベースの作成] ページで指定した説明を変更し、Oracle ログ マイニング データベースの接続情報を変更します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-111">**Oracle**: Use the **Oracle** tab in the Properties editor to make changes to the description you provided in the Create CDC database page in the New Instance wizard and to make changes to the Oracle Log Mining database connection information.</span></span>  
  
         <span data-ttu-id="7d49d-112">このタブで編集できる内容の詳細については、「 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d49d-112">For information about what you can edit in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
    -   <span data-ttu-id="7d49d-113">**[テーブル]** : Oracle ソース データベースから選択したテーブルおよび列を変更するには、 **[テーブル]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-113">**Tables**: Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span>  
  
         <span data-ttu-id="7d49d-114">このタブで編集できる内容の詳細については、「 [Edit Tables](edit-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d49d-114">For information about what you can edit in this tab, see Edit [Edit Tables](edit-tables.md)</span></span>  
  
    -   <span data-ttu-id="7d49d-115">**[スクリプト]** : 補足ログを設定する Oracle ソース データベースでスクリプトを実行または再実行するには、 **[スクリプト]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-115">**Scripts**: Use the **Scripts** tab to run or re-run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
         <span data-ttu-id="7d49d-116">このタブで実行できる内容の詳細については、「 [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d49d-116">For information about what you can do in this tab, see [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).</span></span>  
  
    -   <span data-ttu-id="7d49d-117">**[詳細設定]** : CDC インスタンスに特殊なプロパティを追加するには、 **[詳細設定]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d49d-117">**Advanced**: Use the **Advanced** tab to add special properties to the CDC instance.</span></span>  
  
         <span data-ttu-id="7d49d-118">このタブで実行できる内容の詳細については、「 [Edit the Advanced Properties](edit-the-advanced-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d49d-118">For information about what you can do in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
