---
title: コマンド パラメーター | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646147"
---
# <a name="command-parameters"></a><span data-ttu-id="e5286-102">コマンド パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5286-102">Command Parameters</span></span>
  <span data-ttu-id="e5286-103">コマンド テキスト内のパラメーターは、疑問符文字でマークされます。</span><span class="sxs-lookup"><span data-stu-id="e5286-103">Parameters are marked in command text with the question mark character.</span></span> <span data-ttu-id="e5286-104">たとえば、次の SQL ステートメントでは 1 つの入力パラメーターがマークされています。</span><span class="sxs-lookup"><span data-stu-id="e5286-104">For example, the following SQL statement is marked for a single input parameter:</span></span>  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 <span data-ttu-id="e5286-105">ネットワークトラフィックを減らすことによってパフォーマンスを向上させるために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コマンドの実行前に**ICommandWithParameters:: getparameterinfo**または**ICommandPrepare::P repare**が呼び出されない限り、パラメーター情報を自動的には派生しません。</span><span class="sxs-lookup"><span data-stu-id="e5286-105">To improve performance by reducing network traffic, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically derive parameter information unless **ICommandWithParameters::GetParameterInfo** or **ICommandPrepare::Prepare** is called before executing a command.</span></span> <span data-ttu-id="e5286-106">これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが自動的に実行しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e5286-106">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not automatically:</span></span>  
  
-   <span data-ttu-id="e5286-107">**ICommandWithParameters::SetParameterInfo** で指定されたデータ型の正当性を確認すること。</span><span class="sxs-lookup"><span data-stu-id="e5286-107">Verify the correctness of the data type specified with **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="e5286-108">アクセサー バインド情報で指定された DBTYPE から、そのパラメーターに対する適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にマップすること。</span><span class="sxs-lookup"><span data-stu-id="e5286-108">Map from the DBTYPE specified in the accessor binding information to the correct [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter.</span></span>  
  
 <span data-ttu-id="e5286-109">アプリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型のパラメーターと互換性のないデータ型を指定すると、上記のいずれかが原因で、エラーが発生したり、有効桁数が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5286-109">Applications will receive possible errors or loss of precision with either of these methods if they specify data types that are not compatible with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the parameter.</span></span>  
  
 <span data-ttu-id="e5286-110">このようなことが起きないようにするには、アプリケーションで次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5286-110">To ensure this does not happen, the application should:</span></span>  
  
-   <span data-ttu-id="e5286-111">**ICommandWithParameters::SetParameterInfo** をハードコーディングしている場合、*pwszDataSourceType* をパラメーターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型と一致させます。</span><span class="sxs-lookup"><span data-stu-id="e5286-111">Ensure that *pwszDataSourceType* matches the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding **ICommandWithParameters::SetParameterInfo**.</span></span>  
  
-   <span data-ttu-id="e5286-112">アクセサーをハードコーディングしている場合、パラメーターにバインドされている DBTYPE 値の型を、パラメーターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型と同じにします。</span><span class="sxs-lookup"><span data-stu-id="e5286-112">Ensure that the DBTYPE value being bound to the parameter is of the same type as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the parameter if hard-coding an accessor.</span></span>  
  
-   <span data-ttu-id="e5286-113">**ICommandWithParameters::GetParameterInfo** を呼び出すようにアプリケーションをコーディングし、プロバイダーでパラメーターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を動的に取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e5286-113">Code the application to call **ICommandWithParameters::GetParameterInfo** so that the provider can obtain the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types of the parameters dynamically.</span></span> <span data-ttu-id="e5286-114">これにより、ネットワーク上でサーバーとの余分なやり取りが増えることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e5286-114">Note that this causes an extra network round trip to the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5286-115">SQL Native Client OLE DB プロバイダーでは、FROM 句が含まれている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE ステートメントや DELETE ステートメント、パラメーターを含むサブクエリに依存する SQL ステートメント、比較の両方の式、LIKE 述部、および定量化された述語内にパラメーター マーカーを含む SQL ステートメント、またはパラメーターのいずれかが、関数に対するパラメーターになっているクエリの場合は、**ICommandWithParameters::GetParameterInfo** を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e5286-115">The provider does not support calling **ICommandWithParameters::GetParameterInfo** for any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE or DELETE statement containing a FROM clause; for any SQL statement depending on a subquery containing parameters; for SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate; or queries where one of the parameters is a parameter to a function.</span></span> <span data-ttu-id="e5286-116">また、SQL ステートメントをバッチ処理する場合、バッチ内の最初のステートメントの後にあるステートメント内のパラメーター マーカーに対して、**ICommandWithParameters::GetParameterInfo** を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e5286-116">When processing a batch of SQL statements, the provider also does not support calling **ICommandWithParameters::GetParameterInfo** for parameter markers in statements after the first statement in the batch.</span></span> <span data-ttu-id="e5286-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] コマンド内ではコメント (/\* \*/) を使用できません。</span><span class="sxs-lookup"><span data-stu-id="e5286-117">Comments (/\* \*/) are not allowed in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="e5286-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、SQL ステートメントコマンドで入力パラメーターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e5286-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input parameters in SQL statement commands.</span></span> <span data-ttu-id="e5286-119">プロシージャ呼び出しコマンドでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、入力、出力、入出力のパラメーターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e5286-119">On procedure-call commands, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports input, output, and input/output parameters.</span></span> <span data-ttu-id="e5286-120">出力パラメーターの値は、実行時 (行セットが返されない場合のみ)、または返されたすべての行セットがアプリケーションによって使用されたときにアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="e5286-120">Output parameter values are returned to the application either on execution (only if there are no rowsets returned) or when all returned rowsets are exhausted by the application.</span></span> <span data-ttu-id="e5286-121">返される値が有効であることを保証するには、**IMultipleResults** を使用して行セットを強制的に使用します。</span><span class="sxs-lookup"><span data-stu-id="e5286-121">To ensure that returned values are valid, use **IMultipleResults** to force rowset consumption.</span></span>  
  
 <span data-ttu-id="e5286-122">ストアド プロシージャ パラメーターの名前を DBPARAMBINDINFO 構造体で指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e5286-122">The names of stored procedure parameters need not be specified in a DBPARAMBINDINFO structure.</span></span> <span data-ttu-id="e5286-123">*PwszName*メンバーの値には NULL を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがパラメーター名を無視し、 **ICommandWithParameters:: setparameterinfo**の*rgParamOrdinals*メンバーに指定されている序数のみを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="e5286-123">Use NULL for the value of the *pwszName* member to indicate that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider should ignore the parameter name and use only the ordinal specified in the *rgParamOrdinals* member of **ICommandWithParameters::SetParameterInfo**.</span></span> <span data-ttu-id="e5286-124">コマンド テキストに名前付きのパラメーターと名前のないパラメーターの両方が含まれている場合、どの名前付きパラメーターよりも前に、名前のないパラメーターをすべて指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5286-124">If the command text contains both named and unnamed parameters, all of the unnamed parameters must be specified before any named parameters.</span></span>  
  
 <span data-ttu-id="e5286-125">ストアドプロシージャパラメーターの名前が指定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、その名前が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e5286-125">If the name of a stored procedure parameter is specified, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider checks the name to ensure that it is valid.</span></span> <span data-ttu-id="e5286-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コンシューマーから間違ったパラメーター名を受け取ったときにエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="e5286-126">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error when it receives an erroneous parameter name from the consumer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5286-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML およびユーザー定義型 (UDT) のサポートを公開するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは新しい[Isscommandwithparameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="e5286-127">To expose support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML and user-defined types (UDT), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements a new [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5286-128">参照</span><span class="sxs-lookup"><span data-stu-id="e5286-128">See Also</span></span>  
 [<span data-ttu-id="e5286-129">コマンド</span><span class="sxs-lookup"><span data-stu-id="e5286-129">Commands</span></span>](commands.md)  
  
  
