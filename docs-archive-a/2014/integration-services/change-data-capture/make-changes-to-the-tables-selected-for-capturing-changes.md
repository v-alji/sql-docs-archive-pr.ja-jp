---
title: 変更をキャプチャするために選択したテーブルに対する変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 258eb8e761ac697bebd630cc0e627941b4ffc7d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633971"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a><span data-ttu-id="139a8-102">変更をキャプチャするために選択したテーブルに対する変更</span><span class="sxs-lookup"><span data-stu-id="139a8-102">Make Changes to the Tables Selected for Capturing Changes</span></span>
  <span data-ttu-id="139a8-103">このダイアログ ボックスでは、選択したテーブルから変更をキャプチャする特定の列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="139a8-103">In this dialog box, you can select specific columns from the selected table to capture changes from.</span></span> <span data-ttu-id="139a8-104">**[セキュリティ ロール]** と **[キャプチャ インスタンス]** の情報を編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="139a8-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
 <span data-ttu-id="139a8-105">このダイアログ ボックスでは、変更をキャプチャするために選択したテーブルに次の変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="139a8-105">You can make the following changes to the tables you selected for capturing changes in this dialog box.</span></span>  
  
 <span data-ttu-id="139a8-106">**CDC インスタンスに含める列の変更**</span><span class="sxs-lookup"><span data-stu-id="139a8-106">**Make changes to which columns are included in the CDC instance:**</span></span>  
  
 <span data-ttu-id="139a8-107">次のいずれかまたは両方の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="139a8-107">Do one or both of the following:</span></span>  
  
-   <span data-ttu-id="139a8-108">CDC インスタンスに含める追加の列の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="139a8-108">Select the check box next to any additional column you want to include.</span></span>  
  
-   <span data-ttu-id="139a8-109">CDC インスタンスに含めない列の横のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="139a8-109">Clear the check box next to any column that you no longer want to include.</span></span>  
  
 <span data-ttu-id="139a8-110">**特定の列のデータ型の変更**</span><span class="sxs-lookup"><span data-stu-id="139a8-110">**Change the data type for a specific column**:</span></span>  
  
 <span data-ttu-id="139a8-111">特定の列に別のデータ型を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="139a8-111">You can select a different data type for a specific column.</span></span> <span data-ttu-id="139a8-112">元のデータ型と互換性のあるデータ型への変更のみが可能です。</span><span class="sxs-lookup"><span data-stu-id="139a8-112">You can only change the data type to a data type that is compatible with the original data type.</span></span>  
  
 <span data-ttu-id="139a8-113">データ型を変更するには、 **[データ型]** 列をクリックし、別のデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="139a8-113">To change the data type, click in the **Data Type** column and select a different data type.</span></span> <span data-ttu-id="139a8-114">元のデータ型と互換性のあるデータ型のみを選択できます。</span><span class="sxs-lookup"><span data-stu-id="139a8-114">Only data types that are compatible with the original data type are available.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="139a8-115">他に選択できるデータ型がない場合は、ドロップダウン リストが表示されません。</span><span class="sxs-lookup"><span data-stu-id="139a8-115">If no additional data types can be selected, the drop-down list is not available.</span></span>  
  
 <span data-ttu-id="139a8-116">**セキュリティ ロールの変更**</span><span class="sxs-lookup"><span data-stu-id="139a8-116">**Change the Security Role**</span></span>  
  
 <span data-ttu-id="139a8-117">**"セキュリティ ロール"** フィールドで、セキュリティ ゲーティング ロールの新しい名前を入力するか、既存の名前を編集します。</span><span class="sxs-lookup"><span data-stu-id="139a8-117">Type a new name or edit the name of the security gating role in the **Security Role** field.</span></span>  
  
 <span data-ttu-id="139a8-118">**キャプチャ インスタンスの変更または追加**</span><span class="sxs-lookup"><span data-stu-id="139a8-118">**Change or add a capture instance**</span></span>  
  
 <span data-ttu-id="139a8-119">**"キャプチャ インスタンス"** フィールドに、キャプチャ インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="139a8-119">In the **Capture Instance** field enter a name for the capture instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139a8-120">参照</span><span class="sxs-lookup"><span data-stu-id="139a8-120">See Also</span></span>  
 <span data-ttu-id="139a8-121">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="139a8-121">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="139a8-122">Oracle のテーブルおよび列の選択</span><span class="sxs-lookup"><span data-stu-id="139a8-122">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
