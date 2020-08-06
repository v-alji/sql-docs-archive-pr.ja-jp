---
title: 式を使用したカスタム アセンブリへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99497de0456d90fd522ce27c62fd5aa1b812059f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630799"
---
# <a name="accessing-custom-assemblies-through-expressions"></a><span data-ttu-id="a33e4-102">式を使用したカスタム アセンブリへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a33e4-102">Accessing Custom Assemblies Through Expressions</span></span>
  <span data-ttu-id="a33e4-103">カスタム アセンブリを作成し、レポート デザイナーまたはレポート サーバーで利用可能にします。そして、適切なセキュリティ ポリシーを追加し、レポート定義のカスタム アセンブリへの参照を追加すると、レポートの式を使用してアセンブリ内のクラスのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a33e4-103">Once you have created a custom assembly, made it available to Report Designer or the report server, added the appropriate security policy, and added a reference to your custom assembly in your report definition, you can access the members of the classes in your assembly using report expressions.</span></span> <span data-ttu-id="a33e4-104">式の中でカスタム コードを参照するには、アセンブリ内のクラスのメンバーを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-104">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="a33e4-105">呼び出す方法は、メソッドが静的であるかインスタンス ベースであるかにより異なります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-105">How you do this depends on whether the method is static or instance-based.</span></span>  
  
## <a name="calling-static-members-from-a-report-definition-file"></a><span data-ttu-id="a33e4-106">レポート定義ファイルから静的メンバーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a33e4-106">Calling Static Members from a Report Definition File</span></span>  
 <span data-ttu-id="a33e4-107">静的メンバーはクラスまたは型そのものに所属し、インスタンス化されたオブジェクトには所属しません。</span><span class="sxs-lookup"><span data-stu-id="a33e4-107">Static members belong to the class or type itself and not to an instantiated object.</span></span> <span data-ttu-id="a33e4-108">静的メンバーはクラスから直接呼び出すことによりアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a33e4-108">These members can be accessed by directly calling them from the class.</span></span> <span data-ttu-id="a33e4-109">可能な場合は常に、静的メンバーを使用してレポートのカスタム関数を呼び出す必要があります。その理由は、静的メンバーがパフォーマンス上最も優れているからです。</span><span class="sxs-lookup"><span data-stu-id="a33e4-109">You should use static members to call custom functions in a report whenever possible, because static members perform best.</span></span> <span data-ttu-id="a33e4-110">静的メンバーを呼び出すには、=*Namespace.Class.Method* の形をとる式として参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-110">To call a static member, you need to reference it as an expression that takes the form =*Namespace.Class.Method*.</span></span>  
  
#### <a name="to-call-static-members"></a><span data-ttu-id="a33e4-111">静的メンバーを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a33e4-111">To call static members</span></span>  
  
-   <span data-ttu-id="a33e4-112">静的メンバーを呼び出すには、式と、完全に修飾されたメンバー名とを等しくします。メンバー名を完全に修飾するには、名前空間、クラス名、およびメンバー名を使用します。</span><span class="sxs-lookup"><span data-stu-id="a33e4-112">To call a static member, set your expression equal to the fully qualified name of the member, which includes the namespace, class name, and member name.</span></span> <span data-ttu-id="a33e4-113">次の例では、**ToGBP** メソッドを呼び出します。このメソッドは、**StandardCost** フィールドの値をドルから英ポンドに換算し、レポートに表示します。</span><span class="sxs-lookup"><span data-stu-id="a33e4-113">The following example calls the **ToGBP** method, which converts the **StandardCost** field value from dollars to pounds sterling and displays it in a report:</span></span>  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a><span data-ttu-id="a33e4-114">静的フィールドおよび静的プロパティに関する重要な情報</span><span class="sxs-lookup"><span data-stu-id="a33e4-114">Important Information Regarding Static Fields and Properties</span></span>  
 <span data-ttu-id="a33e4-115">現在のところ、すべてのレポートは同じアプリケーション ドメインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a33e4-115">Currently, all reports are executed in the same application domain.</span></span> <span data-ttu-id="a33e4-116">このことは、レポートのユーザー固有の静的データを、同じレポートの他のインスタンスから参照できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a33e4-116">This means that reports with user-specific, static data expose this data to other instances of the same report.</span></span> <span data-ttu-id="a33e4-117">このような状況では、あるユーザーの静的データを、同時平行して個々のレポートを実行している他のすべてのユーザーが利用できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-117">This condition might make it possible for the static data of one user to be available to all users currently running a particular report.</span></span> <span data-ttu-id="a33e4-118">そのため、カスタム アセンブリまたは **Code** 要素の中で静的フィールドおよび静的プロパティを使用しないよう、強くお勧めします。レポートの中ではインスタンス フィールドおよびインスタンス プロパティを使用してください。</span><span class="sxs-lookup"><span data-stu-id="a33e4-118">For this reason, it is highly recommended that you not use static fields or properties in custom assemblies or in the **Code** element; instead, use instance fields or properties in your reports.</span></span> <span data-ttu-id="a33e4-119">しかし、静的メソッドは、状態やデータを保存しないため、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="a33e4-119">Static methods can still be used, because they do not store state or data.</span></span>  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a><span data-ttu-id="a33e4-120">レポート定義ファイルからインスタンス メンバーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a33e4-120">Calling Instance Members from a Report Definition File</span></span>  
 <span data-ttu-id="a33e4-121">レポート定義内からアクセスする必要があるインスタンス メンバーがカスタム アセンブリ内に含まれている場合は、クラスのインスタンス名をレポートに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-121">If your custom assembly contains instance members that you need to access in a report definition, you must add an instance name for your class to the report.</span></span> <span data-ttu-id="a33e4-122">**[レポートのプロパティ]** ダイアログ ボックスの **[コード]** タブを使用してクラスのインスタンス名を追加できます。</span><span class="sxs-lookup"><span data-stu-id="a33e4-122">You can add an instance name for a class using the **Code** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="a33e4-123">レポートにクラスのインスタンスを追加する方法については、「[レポート デザイナーでカスタム コードやアセンブリを式から参照する &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a33e4-123">For more information about adding instances of classes to a report, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="a33e4-124">静的メンバーを呼び出すには、= Code という形式の式として参照する必要があり*ます。InstanceName. メソッド*。</span><span class="sxs-lookup"><span data-stu-id="a33e4-124">To call a static member, you need to reference it as an expression that takes the form = Code *.InstanceName.Method*.</span></span>  
  
#### <a name="to-call-instance-members"></a><span data-ttu-id="a33e4-125">インスタンス メンバーを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="a33e4-125">To call instance members</span></span>  
  
-   <span data-ttu-id="a33e4-126">カスタム アセンブリのインスタンス メンバーを呼び出すには、キーワード **Code** の後にインスタンス名とメソッドを記述して参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a33e4-126">To call an instance member of a custom assembly, you must reference the **Code** keyword followed by the instance name and the method.</span></span> <span data-ttu-id="a33e4-127">次の例では、インスタンス メソッド **ToEUR** を呼び出します。このメソッドは、**StandardCost** フィールドの値をドルからユーロに換算し、レポートに表示します。</span><span class="sxs-lookup"><span data-stu-id="a33e4-127">The following example calls an instance method **ToEUR** which converts the **StandardCost** field value from dollars to euros and displays it in a report:</span></span>  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a33e4-128">参照</span><span class="sxs-lookup"><span data-stu-id="a33e4-128">See Also</span></span>  
 [<span data-ttu-id="a33e4-129">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="a33e4-129">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
