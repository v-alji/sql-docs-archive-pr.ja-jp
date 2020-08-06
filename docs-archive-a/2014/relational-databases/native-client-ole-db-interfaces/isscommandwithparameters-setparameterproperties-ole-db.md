---
title: ISSCommandWithParameters::SetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- SetParameterProperties method
ms.assetid: 4cd0281a-a2a0-43df-8e46-eb478b64cb4b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bf8e5cde9885a5d9b55d84c6384b76aecf50b8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713114"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a><span data-ttu-id="79c9b-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="79c9b-102">ISSCommandWithParameters::SetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="79c9b-103">序数順に各パラメーターのパラメーター プロパティを設定するか、SSPARAMPROPS 構造体の配列を指定して、一括でパラメーター プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="79c9b-103">Sets the parameter properties on a per parameter basis by ordinal, or sets bulk parameter properties by specifying an array of SSPARAMPROPS structures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="79c9b-104">Syntax</span></span>  
  
```  
  
HRESULT SetParameterProperties(  
DB_UPARAMS cParams,   
SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a><span data-ttu-id="79c9b-105">引数</span><span class="sxs-lookup"><span data-stu-id="79c9b-105">Arguments</span></span>  
 <span data-ttu-id="79c9b-106">*cParams*[in]</span><span class="sxs-lookup"><span data-stu-id="79c9b-106">*cParams*[in]</span></span>  
 <span data-ttu-id="79c9b-107">*rgParamProperties* 配列内の SSPARAMPROPS 構造体の数。</span><span class="sxs-lookup"><span data-stu-id="79c9b-107">The number of SSPARAMPROPS structures in the *rgParamProperties* array.</span></span> <span data-ttu-id="79c9b-108">この数値が0の場合は、 `ISSCommandWithParameters::SetParameterProperties` コマンドのパラメーターに指定されている可能性のあるすべてのプロパティが削除されます。</span><span class="sxs-lookup"><span data-stu-id="79c9b-108">If this number is zero, `ISSCommandWithParameters::SetParameterProperties` will delete all properties that might have been specified for any parameters in the command.</span></span>  
  
 <span data-ttu-id="79c9b-109">*rgParamProperties*[in]</span><span class="sxs-lookup"><span data-stu-id="79c9b-109">*rgParamProperties*[in]</span></span>  
 <span data-ttu-id="79c9b-110">設定する SSPARAMPROPS 構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="79c9b-110">An array of SSPARAMPROPS structures to be set.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="79c9b-111">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="79c9b-111">Return Code Values</span></span>  
 <span data-ttu-id="79c9b-112">この `ISSCommandWithParameters::SetParameterProperties` メソッドは、コア OLE DB **ICommandProperties:: SetProperties**メソッドと同じエラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="79c9b-112">The `ISSCommandWithParameters::SetParameterProperties` method returns the same error codes as the core OLE DB **ICommandProperties::SetProperties** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c9b-113">解説</span><span class="sxs-lookup"><span data-stu-id="79c9b-113">Remarks</span></span>  
 <span data-ttu-id="79c9b-114">このメソッドを使用してパラメーターのプロパティを設定できるのは、序数によってパラメーターごとに指定するか、または `ISSCommandWithParameters::SetParameterProperties` SSPARC AMPROPS がプロパティ配列から構築された1回の呼び出しで許可されます。</span><span class="sxs-lookup"><span data-stu-id="79c9b-114">Setting parameter properties with this method is allowed on a per parameter basis by ordinal, or with a single `ISSCommandWithParameters::SetParameterProperties` call once the SSPARAMPROPS has been built from the property array.</span></span>  
  
 <span data-ttu-id="79c9b-115">メソッドを呼び出す前に**Setparameterinfo**メソッドを呼び出す必要があり `ISSCommandWithParameters::SetParameterProperties` ます。</span><span class="sxs-lookup"><span data-stu-id="79c9b-115">The **SetParameterInfo** method must be called before calling the `ISSCommandWithParameters::SetParameterProperties` method.</span></span> <span data-ttu-id="79c9b-116">`SetParameterProperties(0, NULL)` を呼び出すと、指定したパラメーター プロパティがすべて消去されます。また、`SetParameterInfo(0,NULL,NULL)` を呼び出すと、パラメーターに関連付けられているすべてのプロパティを含めて、パラメーターに関するすべての情報が消去されます。</span><span class="sxs-lookup"><span data-stu-id="79c9b-116">Calling `SetParameterProperties(0, NULL)` clears all specified parameter properties, while calling `SetParameterInfo(0,NULL,NULL)` clears all the parameter info including any properties that might be associated with a parameter.</span></span>  
  
 <span data-ttu-id="79c9b-117">`ISSCommandWithParameters::SetParameterProperties`を呼び出して、DBTYPE_XML 型または DBTYPE_UDT 型ではないパラメーターのプロパティを指定すると、DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が返され、そのパラメーターの SSPARAMPROPS に含まれるすべての dbprops の*dwstatus*フィールドが DBPROPSTATUS_NOTSET でマークされます。</span><span class="sxs-lookup"><span data-stu-id="79c9b-117">Calling `ISSCommandWithParameters::SetParameterProperties` to specify properties for a parameter which is not of type DBTYPE_XML or DBTYPE_UDT returns DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED and marks the *dwStatus* field of all DBPROPs contained in SSPARAMPROPS for that parameter with DBPROPSTATUS_NOTSET.</span></span> <span data-ttu-id="79c9b-118">DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED が指しているパラメーターを検出するには、SSPARAMPROPS に含まれている各 DBPROPSET の DBPROP 配列をすべて調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c9b-118">The DBPROP array of each DBPROPSET contained in SSPARAMPROPS should be traversed to detect which parameter the DB_E_ERRORSOCCURRED or DB_S_ERRORSOCCURRED refers to.</span></span>  
  
 <span data-ttu-id="79c9b-119">`ISSCommandWithParameters::SetParameterProperties`パラメーター情報が**setparameterinfo**でまだ設定されていないパラメーターのプロパティを指定するためにが呼び出された場合、プロバイダーは次のエラーメッセージと共に E_UNEXPECTED を返します。</span><span class="sxs-lookup"><span data-stu-id="79c9b-119">If `ISSCommandWithParameters::SetParameterProperties` is called to specify the properties of parameters whose parameter info have not been set yet with **SetParameterInfo**, the provider returns E_UNEXPECTED with the following error message:</span></span>  
  
 <span data-ttu-id="79c9b-120">パラメーターを指定して SetParameterProperties メソッドを呼び出す場合は、最初に SetParameterInfo メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c9b-120">SetParameterProperties method cannot be called for the specified parameters without first calling SetParameterInfo method.</span></span> <span data-ttu-id="79c9b-121">パラメーターのプロパティを設定する前に、パラメーター情報を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c9b-121">The parameter information must be set before setting the parameter properties.</span></span>  
  
 <span data-ttu-id="79c9b-122">パラメーターヒントが設定されているいくつかのパラメーターと、パラメーター情報が設定されていないパラメーターがの呼び出しに `ISSCommandWithParameters::SetParameterProperties` 含まれている場合、SDBPROPSET AMPROPS プロパティセットの dwStatus プロパティは DBSTATUS_NOTSET を返します。</span><span class="sxs-lookup"><span data-stu-id="79c9b-122">If the call to `ISSCommandWithParameters::SetParameterProperties` contains some parameters where the parameter info has been set, and some parameters where the parameter info has not been set, the dwStatus properties in the DBPROPSET of the SSPARAMPROPS property set will return with DBSTATUS_NOTSET.</span></span>  
  
 <span data-ttu-id="79c9b-123">SSPARAMPROPS 構造体は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="79c9b-123">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 <span data-ttu-id="79c9b-124">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のデータベース エンジンの機能強化により、ISSCommandWithParameters::SetParameterProperties では、期待される結果のより正確な記述を取得できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="79c9b-124">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ISSCommandWithParameters::SetParameterProperties to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="79c9b-125">結果がより正確になり、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で ISSCommandWithParameters::SetParameterProperties から返される値とは異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="79c9b-125">These more accurate results may differ from the values returned by ISSCommandWithParameters::SetParameterProperties in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="79c9b-126">詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c9b-126">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
|<span data-ttu-id="79c9b-127">メンバー</span><span class="sxs-lookup"><span data-stu-id="79c9b-127">Member</span></span>|<span data-ttu-id="79c9b-128">説明</span><span class="sxs-lookup"><span data-stu-id="79c9b-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="79c9b-129">*iOrdinal*</span><span class="sxs-lookup"><span data-stu-id="79c9b-129">*iOrdinal*</span></span>|<span data-ttu-id="79c9b-130">渡されるパラメーターの序数</span><span class="sxs-lookup"><span data-stu-id="79c9b-130">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="79c9b-131">*cPropertySets*</span><span class="sxs-lookup"><span data-stu-id="79c9b-131">*cPropertySets*</span></span>|<span data-ttu-id="79c9b-132">*rgPropertySets* 内の DBPROPSET 構造体の数</span><span class="sxs-lookup"><span data-stu-id="79c9b-132">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="79c9b-133">*rgPropertySets*</span><span class="sxs-lookup"><span data-stu-id="79c9b-133">*rgPropertySets*</span></span>|<span data-ttu-id="79c9b-134">DBPROPSET 構造体の配列を返すメモリへのポインター</span><span class="sxs-lookup"><span data-stu-id="79c9b-134">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79c9b-135">参照</span><span class="sxs-lookup"><span data-stu-id="79c9b-135">See Also</span></span>  
 [<span data-ttu-id="79c9b-136">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="79c9b-136">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
