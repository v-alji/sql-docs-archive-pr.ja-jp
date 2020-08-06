---
title: カスタム アセンブリ オブジェクトの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2aba0bd8b71b26651067a2370728dcdff521ceaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640756"
---
# <a name="initializing-custom-assembly-objects"></a><span data-ttu-id="f4039-102">カスタム アセンブリ オブジェクトの初期化</span><span class="sxs-lookup"><span data-stu-id="f4039-102">Initializing Custom Assembly Objects</span></span>
  <span data-ttu-id="f4039-103">状況によっては、カスタム アセンブリ クラスのプロパティ値とフィールド値をインスタンス化する際、これらを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4039-103">In some cases, you may need to initialize property and field values in your custom assembly classes when you instantiate them.</span></span> <span data-ttu-id="f4039-104">初期化が必要になる可能性が最も高いのは、レポートのグローバル オブジェクト コレクションからカスタム クラスと値を使用する場合です。</span><span class="sxs-lookup"><span data-stu-id="f4039-104">You will most likely need to initialize your custom classes with values available to you from the report's global object collections.</span></span> <span data-ttu-id="f4039-105">そのためには、レポートの **Code** オブジェクトの **OnInit** メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="f4039-105">You do this by overriding the **OnInit** method of the **Code** object of a report.</span></span> <span data-ttu-id="f4039-106">**OnInit** にアクセスするには、レポート定義の **Code** 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4039-106">To access **OnInit**, use the **Code** element of the report definition.</span></span> <span data-ttu-id="f4039-107">レポートで使用する予定のカスタム アセンブリのクラスのプロパティ値またはフィールド値を初期化する方法は 2 つあります。1 つは、**OnInit** を使用してクラスの新しいインスタンスを宣言し、作成する方法、もう 1 つは、**OnInit** を使用してパブリックに使用できるメソッドを呼び出す方法です。</span><span class="sxs-lookup"><span data-stu-id="f4039-107">There are two techniques for initializing property or field values of the classes in a custom assembly that you plan to use in your report: You can either declare and create a new instance of your class using **OnInit**, or you can call a publicly available method using **OnInit**.</span></span>  
  
## <a name="global-object-collections-and-initialization"></a><span data-ttu-id="f4039-108">グローバル オブジェクト コレクションと初期化</span><span class="sxs-lookup"><span data-stu-id="f4039-108">Global Object Collections and Initialization</span></span>  
 <span data-ttu-id="f4039-109">カスタム クラス変数を初期化するときは、</span><span class="sxs-lookup"><span data-stu-id="f4039-109">Several collections are available to you for initializing your custom class variables.</span></span> <span data-ttu-id="f4039-110">**Globals** および **User** の各コレクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4039-110">You can use the **Globals** and **User** collections.</span></span> <span data-ttu-id="f4039-111">レポート ライフサイクルで、**OnInit** メソッドを呼び出す時点では、**Parameters**、**Fields** および **ReportItems** の各コレクションを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f4039-111">The **Parameters**, **Fields** and **ReportItems** collections are not available to you at the point in the report lifecycle when the **OnInit** method is invoked.</span></span> <span data-ttu-id="f4039-112">共有コレクションの **Globals** または **User** を使用するには、**Report** オブジェクト参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4039-112">To use the shared collections, **Globals** or **User**, you need to include the **Report** object reference.</span></span> <span data-ttu-id="f4039-113">たとえば、レポートにアクセスしているユーザーの現在の言語に基づいてカスタム クラスを初期化する場合、**Code** 要素は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f4039-113">For example, to initialize your custom class based on the current language of the user accessing the report, your **Code** element might look like the following:</span></span>  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="f4039-114">前述のように、クラスのプロパティ値とフィールド値を初期化する 1 つの方法は、オーバーライドされたコンストラクターを呼び出すことによってクラスを宣言し、その新しいインスタンスを作成することです。</span><span class="sxs-lookup"><span data-stu-id="f4039-114">One way to initialize the property and field values of a class as shown previously is to declare your class and create a new instance of it by calling an overridden constructor.</span></span>  
  
 <span data-ttu-id="f4039-115">カスタム アセンブリのクラスのプロパティ値とフィールド値を初期化するもう 1 つの方法は、**OnInit** メソッドから定義したパブリックに使用できるメソッドを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="f4039-115">Another way to initialize the property and field values of the classes in your custom assemblies is to call a publicly available method that you define from the **OnInit** method.</span></span> <span data-ttu-id="f4039-116">最初に、レポート定義ファイルのクラスのインスタンス名を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4039-116">You first need to add an instance name for your class in the report definition file.</span></span> <span data-ttu-id="f4039-117">適切なアセンブリ参照とインスタンス名を追加した後は、初期化メソッドを呼び出して、クラスのプロパティ値とフィールド値を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="f4039-117">Once you have added the appropriate assembly reference and instance name, you can call your initialization method to initialize property and field values for your class.</span></span> <span data-ttu-id="f4039-118">**OnInit** メソッドは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f4039-118">Your **OnInit** method might look like the following:</span></span>  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="f4039-119">カスタム クラスのアセンブリ参照とインスタンス名を追加する方法の詳細については、「[レポートにアセンブリへの参照を追加する &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4039-119">For more information about adding an assembly reference and instance name for your custom class, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="f4039-120">グローバル オブジェクト コレクションの詳細については、「[式で使用される組み込みコレクション &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4039-120">For more information about the global object collections, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4039-121">参照</span><span class="sxs-lookup"><span data-stu-id="f4039-121">See Also</span></span>  
 [<span data-ttu-id="f4039-122">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="f4039-122">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
