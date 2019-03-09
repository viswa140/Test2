  public void ValidateCustSummaryInfo(List Customers, List ResRurExpVal, List TermDepsExpVal, List GuaExpVal) {
        json = new JsonPath(response);
        List respVal = new LinkedList();
        int flag = 0;
        int Validateindex = 0;
        int index = 0;

        List CustList = json.getList("customerAndCollateralList");
        for (int i = 0; i < CustList.size(); i++) {
            for (int j = 0; j < Customers.size(); j++) {
                if (json.get("customerAndCollateralList[" + i + "].customerId").equals(Customers.get(j))) {
                    List CollaList = json.getList("customerAndCollateralList[" + i + "].collateralList");
                    CollaLoop:
                    for (int k = 0; k < CollaList.size(); k++) {
                        if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(ResFreeHld) ||
                                json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(ResLeaseHld) ||
                                json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(RurFreeHld) ||
                                json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(RurLeaseHld)) {
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].description"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].ownerList"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].postCode"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].city"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].streetName"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].status"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].propertyType"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].rank"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].priorityGiven"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].managedBy"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].address"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].ownerEstimatedValue"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].marketValue"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].assessmentOfBV"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].assessmentofMV"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].bankValue"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].tenantInterest"));

                            if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(1))) {
                                for (int l = 1; l <= 19; l++) {
                                    Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                    inner:
                                    for (Validateindex = index; Validateindex < Lsize.size(); Validateindex++) {
                                        Assert.assertEquals(respVal.get(Validateindex), ResRurExpVal.get(l));
                                        index++;
                                        break inner;
                                    }
                                }
                                index = 0;
                                if (CollaList.size() > 1) {
                                    if ((CollaList.size() - 1) < k) {
                                        continue CollaLoop;
                                    }
                                }
                            }

                            if (ResRurExpVal.size() > 21) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(21))) {
                                    for (int m = 21; m <= 40; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }
                            if (ResRurExpVal.size() > 41) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(41))) {
                                    for (int m = 41; m <= 60; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }
                            if (ResRurExpVal.size() > 61) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(61))) {
                                    for (int m = 61; m <= 80; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (ResRurExpVal.size() > 81) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(81))) {
                                    for (int m = 81; m <= 100; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (ResRurExpVal.size() > 101) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(101))) {
                                    for (int m = 101; m <= 120; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (ResRurExpVal.size() > 121) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(121))) {
                                    for (int m = 121; m <= 140; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (ResRurExpVal.size() > 141) {
                                if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId").equals(ResRurExpVal.get(141))) {
                                    for (int m = 141; m <= 160; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), ResRurExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }
                        }

                        if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(TermNAB) ||
                                json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(TermNNAB)) {
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].description"));

                            if (respVal.get(1).equals(TermDepsExpVal.get(1))) {
                                for (int l = 1; l <= 19; l++) {
                                    Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                    inner:
                                    for (Validateindex = index; Validateindex < Lsize.size(); Validateindex++) {
                                        Assert.assertEquals(respVal.get(Validateindex), TermDepsExpVal.get(l));
                                        index++;
                                        break inner;
                                    }
                                }
                                index = 0;
                                if (CollaList.size() > 1) {
                                    if ((CollaList.size() - 1) < k) {
                                        continue CollaLoop;
                                    }
                                }
                            }

                            if (TermDepsExpVal.size() > 21) {
                                if (respVal.get(1).equals(TermDepsExpVal.get(21))) {
                                    for (int m = 21; m <= 40; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), TermDepsExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (TermDepsExpVal.size() > 41) {
                                if (respVal.get(1).equals(TermDepsExpVal.get(41))) {
                                    for (int m = 41; m <= 60; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), TermDepsExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }

                            if (TermDepsExpVal.size() > 61) {
                                if (respVal.get(1).equals(TermDepsExpVal.get(61))) {
                                    for (int m = 61; m <= 80; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), TermDepsExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }
                        }

                        if (json.get("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType").equals(Gua)) {
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityId"));
                            respVal.add(json.getString("customerAndCollateralList[" + i + "].collateralList[" + k + "].securityType"));

                            if (respVal.get(1).equals(GuaExpVal.get(1))) {
                                for (int l = 1; l <= 19; l++) {
                                    Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                    inner:
                                    for (Validateindex = index; Validateindex < Lsize.size(); Validateindex++) {
                                        Assert.assertEquals(respVal.get(Validateindex), GuaExpVal.get(l));
                                        index++;
                                        break inner;
                                    }
                                }
                                index = 0;
                                if (CollaList.size() > 1) {
                                    if ((CollaList.size() - 1) < k) {
                                        continue CollaLoop;
                                    }
                                }
                            }

                            if (GuaExpVal.size() > 21) {
                                if (respVal.get(1).equals(GuaExpVal.get(21))) {
                                    for (int m = 21; m <= 40; m++) {
                                        Map Lsize = json.getMap("customerAndCollateralList[" + i + "].collateralList[" + k + "]");
                                        inner:
                                        for (int Validateindex2 = index; Validateindex2 < Lsize.size(); Validateindex2++) {
                                            Assert.assertEquals(respVal.get(Validateindex2), GuaExpVal.get(m));
                                            index++;
                                            break inner;
                                        }
                                    }
                                    index = 0;
                                    if (CollaList.size() > 1) {
                                        if ((CollaList.size() - 1) < k) {
                                            continue CollaLoop;
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
                else {
                    flag++;
                    if (flag == CustList.size()) {
                        Assert.fail("One or More Non Requested customers are present in the response");
                    }
                }
            }

        }
    }
