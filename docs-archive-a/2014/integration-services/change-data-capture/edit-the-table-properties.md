---
title: テーブルのプロパティの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1ba0809b99474704ec0e93e417a04d776bb26d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633976"
---
# <a name="edit-the-table-properties"></a><span data-ttu-id="20daa-102">テーブルのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="20daa-102">Edit the Table Properties</span></span>
  <span data-ttu-id="20daa-103">変更がキャプチャされている選択したテーブルの特定の列を編集するには、このダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="20daa-103">Use this dialog box to edit the specific columns from the selected table where changes are being captured.</span></span> <span data-ttu-id="20daa-104">**[セキュリティ ロール]** と **[キャプチャ インスタンス]** の情報を編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="20daa-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a><span data-ttu-id="20daa-105">CDC インスタンスに含める列を編集するには</span><span class="sxs-lookup"><span data-stu-id="20daa-105">To edit the columns to include in the CDC instance</span></span>  
  
1.  <span data-ttu-id="20daa-106">次のいずれかまたは両方の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="20daa-106">Do one or both of the following:</span></span>  
  
    -   <span data-ttu-id="20daa-107">CDC インスタンスに含める追加の列の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="20daa-107">Select the check box next to any additional column you want to include.</span></span>  
  
    -   <span data-ttu-id="20daa-108">CDC インスタンスに含めない列の横のチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="20daa-108">Clear the check box next to any column that you no longer want to include.</span></span>  
  
### <a name="to-edit-the-security-role"></a><span data-ttu-id="20daa-109">セキュリティ ロールを編集するには</span><span class="sxs-lookup"><span data-stu-id="20daa-109">To edit the Security Role</span></span>  
  
1.  <span data-ttu-id="20daa-110">**"セキュリティ ロール"** フィールドで、新しい名前を入力するか、セキュリティ ロールの名前を編集します。</span><span class="sxs-lookup"><span data-stu-id="20daa-110">Type a new name or edit the name of the security role in the **Security Role** field.</span></span>  
  
### <a name="to-create-a-new-capture-instance"></a><span data-ttu-id="20daa-111">新しいキャプチャ インスタンスを作成するには</span><span class="sxs-lookup"><span data-stu-id="20daa-111">To create a new capture instance</span></span>  
  
1.  <span data-ttu-id="20daa-112">**[セキュリティ ロール]** セクションの **"名前"** フィールドに、キャプチャ インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="20daa-112">In the **Security Role** section, **Name** field enter a name for the capture instance.</span></span> <span data-ttu-id="20daa-113">既定では、このフィールドに入力される名前は、現在のキャプチャ インスタンスの名前の末尾に **_NEW** を追加したものです (例: **old_instance_NEW**)。</span><span class="sxs-lookup"><span data-stu-id="20daa-113">By default, the name entered in the field is the name of the current capture instance with **_NEW** added to the end of the name (for example, **old_instance_NEW**).</span></span>  
  
2.  <span data-ttu-id="20daa-114">キャプチャ インスタンスを次のいずれかとして保存します。</span><span class="sxs-lookup"><span data-stu-id="20daa-114">Save the capture instance as one of the following:</span></span>  
  
    -   <span data-ttu-id="20daa-115">**[新しいキャプチャ インスタンス]** : この場合、新しいキャプチャ インスタンスが保存され、古いキャプチャ インスタンスは削除されません。</span><span class="sxs-lookup"><span data-stu-id="20daa-115">**New Capture Instance**: In this case a new capture instance is saved and the old capture instance is not deleted.</span></span>  
  
         <span data-ttu-id="20daa-116">**注**: テーブルごとに 2 つまでのキャプチャ インスタンスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="20daa-116">**Note**: You can have no more than two capture instances per table.</span></span> <span data-ttu-id="20daa-117">既に 2 つのキャプチャ インスタンスがある場合、このオプションは利用できません。</span><span class="sxs-lookup"><span data-stu-id="20daa-117">If there are already two capture instances, this option is not available.</span></span>  
  
    -   <span data-ttu-id="20daa-118">**[既存のものを置換]** : この場合、現在のキャプチャ インスタンスが削除され、作成したキャプチャ インスタンスで置換されます。</span><span class="sxs-lookup"><span data-stu-id="20daa-118">**Replace Existing**: In this case the current capture instance is deleted and replaced by the capture instance you created.</span></span> <span data-ttu-id="20daa-119">このテーブルに 2 つのキャプチャ インスタンスが定義されている場合、置換するキャプチャ インスタンスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20daa-119">If there are two capture instances defined for this table, you must select one to replace.</span></span>  
  
 <span data-ttu-id="20daa-120">**注**: **[テーブル]** タブのテーブルの一覧からキャプチャ インスタンスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="20daa-120">**Note**: You can remove a capture instance from the list of tables in the **Table** tab.</span></span>  
  
 <span data-ttu-id="20daa-121">このダイアログ ボックスで情報の入力を終了したら、 **[OK]** をクリックして変更を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="20daa-121">After you finish entering the information in this dialog box, click **OK** to accept the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20daa-122">参照</span><span class="sxs-lookup"><span data-stu-id="20daa-122">See Also</span></span>  
 <span data-ttu-id="20daa-123">[CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="20daa-123">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="20daa-124">変更をキャプチャするために選択したテーブルに対する変更</span><span class="sxs-lookup"><span data-stu-id="20daa-124">Make Changes to the Tables Selected for Capturing Changes</span></span>](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  
