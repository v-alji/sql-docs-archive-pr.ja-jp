---
title: ISSCommandWithParameters::GetParameterProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: rothja
ms.author: jroth
ms.openlocfilehash: 2160c93748375a4aa3bee3d530d441182204134a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634495"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a><span data-ttu-id="b5b92-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b5b92-102">ISSCommandWithParameters::GetParameterProperties (OLE DB)</span></span>
  <span data-ttu-id="b5b92-103">SSPARAMPROPS プロパティ セット構造体の配列を返します。各 UDT または XML パラメーターごとに 1 つの SSPARAMPROPS プロパティ セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="b5b92-103">Returns an array of SSPARAMPROPS property set structures, one SSPARAMPROPS property set for each UDT or XML parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5b92-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5b92-104">Syntax</span></span>  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5b92-105">引数</span><span class="sxs-lookup"><span data-stu-id="b5b92-105">Arguments</span></span>  
 <span data-ttu-id="b5b92-106">*pcParams*[out][in]</span><span class="sxs-lookup"><span data-stu-id="b5b92-106">*pcParams*[out][in]</span></span>  
 <span data-ttu-id="b5b92-107">*prgParamProperties* に返された SSPARAMPROPS 構造体の数を保持するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5b92-107">A pointer to memory that contains the number of SSPARAMPROPS structures returned in *prgParamProperties*.</span></span>  
  
 <span data-ttu-id="b5b92-108">*prgParamProperties*[out]</span><span class="sxs-lookup"><span data-stu-id="b5b92-108">*prgParamProperties*[out]</span></span>  
 <span data-ttu-id="b5b92-109">SSPARAMPROPS 構造体の配列が返されるメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5b92-109">A pointer to memory in which an array of SSPARAMPROPS structures is returned.</span></span> <span data-ttu-id="b5b92-110">プロバイダーは、構造体にメモリを割り当て、このメモリにアドレスを返します。コンシューマーは、構造が不要になったときに、 **Imalloc:: Free**を使用してこのメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-110">The provider allocates memory for the structures and returns the address to this memory; the consumer releases this memory with **IMalloc::Free** when it no longer needs the structures.</span></span> <span data-ttu-id="b5b92-111">*PrgParamProperties*の**Imalloc:: Free**を呼び出す前に、コンシューマーは、バリアントに参照型 (BSTR など) が含まれている場合にメモリリークを防ぐために、各 DBPROP 構造体の*Vvalue*プロパティに対して**VariantClear**を呼び出す必要があります。出力時に*Pcparams*がゼロの場合、または DB_E_ERRORSOCCURRED 以外のエラーが発生した場合、プロバイダーはメモリを割り当てず、出力時に*prgParamProperties*が null ポインターであることを保証します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-111">Before calling **IMalloc::Free** for *prgParamProperties*, the consumer must also call **VariantClear** for the *vValue* property of each DBPROP structure in order to prevent a memory leak in cases where the variant contains a reference type (such as a BSTR.) If *pcParams* is zero on output or an error other than DB_E_ERRORSOCCURRED occurs, the provider does not allocate any memory and ensures that *prgParamProperties* is a null pointer on output.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="b5b92-112">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="b5b92-112">Return Code Values</span></span>  
 <span data-ttu-id="b5b92-113">**Getparameterproperties**メソッドは、DB_S_ERRORSOCCURRED と DB_E_ERRORSOCCURED を発生させることができない点を除いて、Core OLE DB **ICommandProperties:: GetProperties**メソッドと同じエラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-113">The **GetParameterProperties** method returns the same error codes as the core OLE DB **ICommandProperties::GetProperties** method, except that DB_S_ERRORSOCCURRED and DB_E_ERRORSOCCURED cannot be raised.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5b92-114">解説</span><span class="sxs-lookup"><span data-stu-id="b5b92-114">Remarks</span></span>  
 <span data-ttu-id="b5b92-115">**Isscommandwithparameters:: GetParameterProperties**は、 **getparameterinfo**に関して一貫して動作します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-115">**ISSCommandWithParameters::GetParameterProperties** behaves consistently with respect to **GetParameterInfo**.</span></span> <span data-ttu-id="b5b92-116">[Isscommandwithparameters:: SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md)または**setparameterinfo**が呼び出されていないか、または cparams が0と等しい場合に呼び出された場合、 **getparameterinfo**はパラメーター情報を取得し、これを返します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-116">If [ISSCommandWithParameters::SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) or **SetParameterInfo** have not been called or have been called with cParams equal to zero, **GetParameterInfo** derives parameter information and returns this.</span></span> <span data-ttu-id="b5b92-117">**Isscommandwithparameters:: setparameterproperties**または**setparameterinfo**が少なくとも1つのパラメーターに対して呼び出されている場合、 **Isscommandwithparameters:: Getparameterproperties**は、 **isscommandwithparameters:: setparameterproperties**が呼び出されたパラメーターに対してのみプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="b5b92-117">If **ISSCommandWithParameters::SetParameterProperties** or **SetParameterInfo** have been called for at least one parameter, **ISSCommandWithParameters::GetParameterProperties** returns properties only for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span> <span data-ttu-id="b5b92-118">Isscommandwithparameters:: **getparameterproperties**または**getparameterinfo**の後に Isscommandwithparameters **:: setparameterproperties**を呼び出すと、Isscommandwithparameters:: **getparameterproperties**の後続の呼び出しで、 **isscommandwithparameters:: setparameterproperties**が呼び出されたこれらのパラメーターのオーバーライドされた値が返されます。</span><span class="sxs-lookup"><span data-stu-id="b5b92-118">If **ISSCommandWithParameters::SetParameterProperties** is called after **ISSCommandWithParameters::GetParameterProperties** or **GetParameterInfo**, subsequent calls to **ISSCommandWithParameters::GetParameterProperties** return the overridden values for those parameters for which **ISSCommandWithParameters::SetParameterProperties** has been called.</span></span>  
  
 <span data-ttu-id="b5b92-119">SSPARAMPROPS 構造体は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="b5b92-119">The SSPARAMPROPS structure is defined as follows:</span></span>  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|<span data-ttu-id="b5b92-120">メンバー</span><span class="sxs-lookup"><span data-stu-id="b5b92-120">Member</span></span>|<span data-ttu-id="b5b92-121">説明</span><span class="sxs-lookup"><span data-stu-id="b5b92-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b5b92-122">*iOrdinal*</span><span class="sxs-lookup"><span data-stu-id="b5b92-122">*iOrdinal*</span></span>|<span data-ttu-id="b5b92-123">渡されるパラメーターの序数</span><span class="sxs-lookup"><span data-stu-id="b5b92-123">The ordinal of the passed parameter.</span></span>|  
|<span data-ttu-id="b5b92-124">*cPropertySets*</span><span class="sxs-lookup"><span data-stu-id="b5b92-124">*cPropertySets*</span></span>|<span data-ttu-id="b5b92-125">*rgPropertySets* 内の DBPROPSET 構造体の数</span><span class="sxs-lookup"><span data-stu-id="b5b92-125">The number of DBPROPSET structures in *rgPropertySets*.</span></span>|  
|<span data-ttu-id="b5b92-126">*rgPropertySets*</span><span class="sxs-lookup"><span data-stu-id="b5b92-126">*rgPropertySets*</span></span>|<span data-ttu-id="b5b92-127">DBPROPSET 構造体の配列を返すメモリへのポインター</span><span class="sxs-lookup"><span data-stu-id="b5b92-127">A pointer to memory in which to return an array of DBPROPSET structures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5b92-128">参照</span><span class="sxs-lookup"><span data-stu-id="b5b92-128">See Also</span></span>  
 [<span data-ttu-id="b5b92-129">ISSCommandWithParameters &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b5b92-129">ISSCommandWithParameters &#40;OLE DB&#41;</span></span>](isscommandwithparameters-ole-db.md)  
  
  
