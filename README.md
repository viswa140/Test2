public void ValidateCustSummaryInfo(List Customers, List ResRurExpVal, List TermDepsExpVal, List GuaExpVal){
        json =  new JsonPath(response);
       List respVal = new LinkedList();
        int flag = 0;
        int Validateindex =0;
        int index =0;

        List CustList = json.getList("customerAndCollateralList");
        for(int i=0;i<CustList.size();i++){
            for(int j=0;j<Customers.size();j++){
                if(json.get("customerAndCollateralList["+i+"].customerId").equals(Customers.get(j))){
                    List CollaList = json.getList("customerAndCollateralList["+i+"].collateralList");
                 CollaLoop:   for(int k=0;k<CollaList.size();k++){
                        if(json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(ResFreeHld) ||
                                json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(ResLeaseHld) ||
                                json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(RurFreeHld) ||
                                json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(RurLeaseHld)) {
                            respVal.add(json.getString("customerAndCollateralList["+i+"].collateralList["+k+"].securityId"));
                            respVal.add(json.getString("customerAndCollateralList["+i+"].collateralList["+k+"].description"));

                            if(json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(ResRurExpVal.get(1))){
                               for(int l =1;l<=19;l++){
                              inner:     for(Validateindex = index; Validateindex<respVal.size();Validateindex++){
                                       Assert.assertEquals(respVal.get(Validateindex) , ResRurExpVal.get(l));
                                       index++;
                                       break inner;
                                   }
                               }
                               index =0;
                               if(CollaList.size() >1 ){
                                   if((CollaList.size()-1) < k){
                                       continue CollaLoop;
                                   }
                               }
                            }

                                if(ResRurExpVal.size() > 21){
                                    if(json.get("customerAndCollateralList["+i+"].collateralList["+k+"].securityType").equals(ResRurExpVal.get(21))){
                                        for(int m = 21; m<=40;m++){
                                            inner: for(int Validateindex2 = index; Validateindex2<respVal.size();Validateindex2++ ){
                                                Assert.assertEquals(respVal.get(Validateindex2) , ResRurExpVal.get(m));
                                                index++;
                                                break inner;
                                            }
                                        }
                                        index = 0;
                                    }
                                }
                        }
                    }
                }
                else {
                    flag++;
                    if(flag == CustList.size()){
                        Assert.fail("One or More Non Requested customers are present in the response");
                    }

                }
            }
        }

    }
