---
title: データベースオブジェクトの操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14dd0c0175a23f809fc925c5104ac15ac408805b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739661"
---
# <a name="working-with-database-objects"></a><span data-ttu-id="ec17e-102">データベース オブジェクトでの作業</span><span class="sxs-lookup"><span data-stu-id="ec17e-102">Working with Database Objects</span></span>
  <span data-ttu-id="ec17e-103">SMO オブジェクトの作成には次の段階があります。</span><span class="sxs-lookup"><span data-stu-id="ec17e-103">The stages of SMO object creation are as follows:</span></span>  
  
1.  <span data-ttu-id="ec17e-104">オブジェクトのインスタンスの作成。</span><span class="sxs-lookup"><span data-stu-id="ec17e-104">Create an instance of the object.</span></span>  
  
2.  <span data-ttu-id="ec17e-105">オブジェクト プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="ec17e-105">Set the object properties.</span></span>  
  
3.  <span data-ttu-id="ec17e-106">子オブジェクトのインスタンスの作成。</span><span class="sxs-lookup"><span data-stu-id="ec17e-106">Create instances of the child objects.</span></span>  
  
4.  <span data-ttu-id="ec17e-107">子オブジェクト プロパティの設定。</span><span class="sxs-lookup"><span data-stu-id="ec17e-107">Set the child object properties.</span></span>  
  
5.  <span data-ttu-id="ec17e-108">オブジェクトの作成。</span><span class="sxs-lookup"><span data-stu-id="ec17e-108">Create the object.</span></span>  
  
 <span data-ttu-id="ec17e-109">SMO アプリケーションで SMO オブジェクトのインスタンスを作成する場合、`Create` メソッドが発行されるまでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上にこれらのインスタンスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="ec17e-109">When instances of SMO objects are created in an SMO application, they do not exist on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] until the `Create` method is issued.</span></span> <span data-ttu-id="ec17e-110">ただし、個々のオブジェクトに対して `Create` メソッドを発行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ec17e-110">However, it is not necessary to issue a `Create` method for every individual object.</span></span> <span data-ttu-id="ec17e-111">オブジェクトに一連の子オブジェクトがある場合、`Create` メソッドを実行するには親オブジェクトのみが必要となります。</span><span class="sxs-lookup"><span data-stu-id="ec17e-111">If an object has a set of child objects, only the parent object is required to run the `Create` method.</span></span> <span data-ttu-id="ec17e-112">たとえば、テーブルの定義には、テーブルに含まれている列が 1 つ以上必要になります。</span><span class="sxs-lookup"><span data-stu-id="ec17e-112">For example, the definition of a table requires that it contains at least one column to exist.</span></span> <span data-ttu-id="ec17e-113">一方、テーブルがなくては列が独立して存在することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec17e-113">Also, a column cannot exist in isolation without a table.</span></span> <span data-ttu-id="ec17e-114">テーブルとテーブルの列の間には共存関係があります。</span><span class="sxs-lookup"><span data-stu-id="ec17e-114">There is a codependent relationship between the table and its columns.</span></span>  
  
 <span data-ttu-id="ec17e-115"><xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> メソッドを使用すると、オブジェクトへの変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ec17e-115">The <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> method lets you make changes to an object.</span></span> <span data-ttu-id="ec17e-116">オブジェクト コレクションの 1 つへの子オブジェクトの追加や、プロパティ値の変更など、1 つのオブジェクトに対する複数の変更は、バッチ化されて 1 つの変更として実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec17e-116">Several changes to an object, such as adding child objects to one of the object's collections or changing a property value, are batched together and run as one.</span></span> <span data-ttu-id="ec17e-117">`Alter` メソッドを使用することによって、ネットワーク トラフィックが減少し、全体のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="ec17e-117">The `Alter` method reduces network traffic and improves overall performance.</span></span>  
  
 <span data-ttu-id="ec17e-118">オブジェクトを削除するには、`Drop` ステートメントを使用します。このとき、そのオブジェクトの初期作成時に要した、共存関係にある子オブジェクトもすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="ec17e-118">The `Drop` statement is used to remove an object and all its codependent child objects that were required to create the object initially.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec17e-119">参照</span><span class="sxs-lookup"><span data-stu-id="ec17e-119">See Also</span></span>  
 [<span data-ttu-id="ec17e-120">SMO オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="ec17e-120">SMO Object Model</span></span>](../smo-object-model.md)  
  
  
