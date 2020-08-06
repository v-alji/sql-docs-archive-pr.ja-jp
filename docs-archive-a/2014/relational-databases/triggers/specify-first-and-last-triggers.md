---
title: 最初と最後のトリガーの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- first triggers [SQL Server]
- last triggers
- DML triggers, first or last triggers
- INSTEAD OF triggers
- AFTER triggers
ms.assetid: 9e6c7684-3dd3-46bb-b7be-523b33fae4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ddb352b00dc759362c8f6ef1e861e55b6f184f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644877"
---
# <a name="specify-first-and-last-triggers"></a><span data-ttu-id="385f8-102">最初と最後のトリガーの指定</span><span class="sxs-lookup"><span data-stu-id="385f8-102">Specify First and Last Triggers</span></span>
  <span data-ttu-id="385f8-103">テーブルに関連付けられている AFTER トリガーの 1 つを、INSERT、DELETE、および UPDATE の各トリガー動作に対して起動される、最初の AFTER トリガーまたは最後の AFTER トリガーのいずれかに指定できます。</span><span class="sxs-lookup"><span data-stu-id="385f8-103">You can specify that one of the AFTER triggers associated with a table be either the first AFTER trigger or the last AFTER trigger that is fired for each INSERT, DELETE, and UPDATE triggering actions.</span></span> <span data-ttu-id="385f8-104">最初と最後のトリガーの間で起動される AFTER トリガーは、任意の順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="385f8-104">The AFTER triggers that are fired between the first and last triggers are executed in undefined order.</span></span>  
  
 <span data-ttu-id="385f8-105">AFTER トリガーの順序を指定するには、 **sp_settriggerorder** ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="385f8-105">To specify the order for an AFTER trigger, use the **sp_settriggerorder** stored procedure.</span></span> <span data-ttu-id="385f8-106">**sp_settriggerorder** には次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="385f8-106">**sp_settriggerorder** has the following options.</span></span>  
  
|<span data-ttu-id="385f8-107">オプション</span><span class="sxs-lookup"><span data-stu-id="385f8-107">Option</span></span>|<span data-ttu-id="385f8-108">説明</span><span class="sxs-lookup"><span data-stu-id="385f8-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="385f8-109">**First**</span><span class="sxs-lookup"><span data-stu-id="385f8-109">**First**</span></span>|<span data-ttu-id="385f8-110">DML トリガーが、トリガー動作に対して起動される最初の AFTER トリガーであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="385f8-110">Specifies that the DML trigger is the first AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="385f8-111">**Last**</span><span class="sxs-lookup"><span data-stu-id="385f8-111">**Last**</span></span>|<span data-ttu-id="385f8-112">DML トリガーが、トリガー動作に対して起動される最後の AFTER トリガーであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="385f8-112">Specifies that the DML trigger is the last AFTER trigger fired for a triggering action.</span></span>|  
|<span data-ttu-id="385f8-113">**なし**</span><span class="sxs-lookup"><span data-stu-id="385f8-113">**None**</span></span>|<span data-ttu-id="385f8-114">DML トリガーを起動する特定の順番がないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="385f8-114">Specifies that there is no specific order in which the DML trigger should be fired.</span></span> <span data-ttu-id="385f8-115">主に最初または最後のトリガーのいずれかの順序をリセットするときに使用します。</span><span class="sxs-lookup"><span data-stu-id="385f8-115">Used mainly to reset a trigger from being either first or last.</span></span>|  
  
 <span data-ttu-id="385f8-116">次の例は、 **sp_settriggerorder**を使用する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="385f8-116">The following example shows using **sp_settriggerorder**:</span></span>  
  
```  
sp_settriggerorder @triggername = 'MyTrigger', @order = 'first', @stmttype = 'UPDATE'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="385f8-117">最初のトリガーと最後のトリガーは、2 つの異なる DML トリガーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="385f8-117">The first and last triggers must be two different DML triggers.</span></span>  
  
 <span data-ttu-id="385f8-118">テーブルでは、INSERT、UPDATE、および DELETE の各トリガーを同時に定義することができます。</span><span class="sxs-lookup"><span data-stu-id="385f8-118">A table can have INSERT, UPDATE, and DELETE triggers defined on it at the same time.</span></span> <span data-ttu-id="385f8-119">各ステートメントはその型ごとに、固有の最初と最後のトリガーを持つことができますが、最初と最後に同じトリガーを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="385f8-119">Each statement type can have its own first and last triggers, but they cannot be the same triggers.</span></span>  
  
 <span data-ttu-id="385f8-120">1 つのテーブルに定義された最初のトリガーまたは最後のトリガーが、FOR UPDATE、FOR DELETE、または FOR INSERT などのトリガー動作に対応していない場合は、それらの動作に対する最初のトリガーまたは最後のトリガーを設定できません。</span><span class="sxs-lookup"><span data-stu-id="385f8-120">If the first or last trigger defined for a table does not cover a triggering action, such as not covering FOR UPDATE, FOR DELETE, or FOR INSERT, there is no first or last trigger for the missing actions.</span></span>  
  
 <span data-ttu-id="385f8-121">INSTEAD OF トリガーは最初のトリガーまたは最後のトリガーとして指定できません。</span><span class="sxs-lookup"><span data-stu-id="385f8-121">INSTEAD OF triggers cannot be specified as first or last triggers.</span></span> <span data-ttu-id="385f8-122">INSTEAD OF トリガーは基になるテーブルが更新される前に起動されるためです。</span><span class="sxs-lookup"><span data-stu-id="385f8-122">INSTEAD OF triggers are fired before updates are made to the underlying tables.</span></span> <span data-ttu-id="385f8-123">INSTEAD OF トリガーによって基になるテーブルが更新された場合、テーブルで定義された AFTER トリガーが起動される前に更新が発生します。</span><span class="sxs-lookup"><span data-stu-id="385f8-123">If updates are made by an INSTEAD OF trigger to underlying tables, the updates occur before any AFTER triggers defined on the table are fired.</span></span> <span data-ttu-id="385f8-124">たとえば、ビュー上の INSTEAD OF INSERT トリガーによってベース テーブルにデータが挿入され、ベース テーブル自体に INSTEAD OF INSERT トリガーおよび 3 つの AFTER INSERT トリガーが含まれる場合、挿入操作の代わりに、ベース テーブルにある INSTEAD OF INSERT トリガーが起動されます。また、ベース テーブルでの挿入操作の後、ベース テーブルにある AFTER トリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="385f8-124">For example, if an INSTEAD OF INSERT trigger on a view inserts data into a base table and the base table itself contains an INSTEAD OF INSERT trigger and three AFTER INSERT triggers, the INSTEAD OF INSERT trigger on the base table is fired instead of the inserting action, and the AFTER triggers on the base table are fired after any inserting action on the base table.</span></span> <span data-ttu-id="385f8-125">詳しくは、「 [DML Triggers](dml-triggers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="385f8-125">For more information, see [DML Triggers](dml-triggers.md).</span></span>  
  
 <span data-ttu-id="385f8-126">ALTER TRIGGER ステートメントによって最初のトリガーまたは最後のトリガーが変更された場合、 **First** 属性または **Last** 属性が削除され、順序の値が **None**に設定されます。</span><span class="sxs-lookup"><span data-stu-id="385f8-126">If an ALTER TRIGGER statement changes a first or last trigger, the **First** or **Last** attribute is dropped and the order value is set to **None**.</span></span> <span data-ttu-id="385f8-127">**sp_settriggerorder**を使用して順序をリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="385f8-127">The order must be reset by using **sp_settriggerorder**.</span></span>  
  
 <span data-ttu-id="385f8-128">OBJECTPROPERTY 関数は、トリガーが最初のトリガーであるか、または最後のトリガーであるかを、 **ExecIsFirstTrigger** プロパティおよび **ExecIsLastTrigger**プロパティを使用して示します。</span><span class="sxs-lookup"><span data-stu-id="385f8-128">The OBJECTPROPERTY function reports whether a trigger is a first or last trigger by using the properties **ExecIsFirstTrigger** and **ExecIsLastTrigger**.</span></span>  
  
 <span data-ttu-id="385f8-129">レプリケーションは、テーブルが即時更新サブスクリプションまたはキュー更新サブスクリプションに含まれる場合、自動的に最初のトリガーを生成します。</span><span class="sxs-lookup"><span data-stu-id="385f8-129">Replication automatically generates a first trigger for any table that is included in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="385f8-130">レプリケーションのトリガーは最初のトリガーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="385f8-130">Replication requires that its trigger be the first trigger.</span></span> <span data-ttu-id="385f8-131">レプリケーションでは、最初のトリガーを持つテーブルを即時更新サブスクリプションまたはキュー更新サブスクリプションに含めるよう設定すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="385f8-131">Replication raises an error when you try to include a table with a first trigger in an immediate updating or queued updating subscription.</span></span> <span data-ttu-id="385f8-132">テーブルをサブスクリプションに含めた後、トリガーを最初のトリガーに設定すると、 **sp_settriggerorder** はエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="385f8-132">If you try to make a trigger a first trigger after a table has been included in a subscription, **sp_settriggerorder** returns an error.</span></span> <span data-ttu-id="385f8-133">レプリケーション トリガーに ALTER を使用したり、 **sp_settriggerorder** を使用してレプリケーション トリガーを最後のトリガーまたは順序なしのトリガーに変更すると、サブスクリプションは正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="385f8-133">If you use ALTER on the replication trigger or use **sp_settriggerorder** to change the replication trigger to a last or none trigger, the subscription will not function correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385f8-134">参照</span><span class="sxs-lookup"><span data-stu-id="385f8-134">See Also</span></span>  
 <span data-ttu-id="385f8-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="385f8-135">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="385f8-136">sp_settriggerorder &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="385f8-136">sp_settriggerorder &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql)  
  
  
