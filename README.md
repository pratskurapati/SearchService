package com.search.elasticsearch.controller;

import com.search.elasticsearch.model.DataAsset;
import com.search.elasticsearch.service.DataAssetService;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;


import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

import static com.search.elasticsearch.controller.DataAssetController.dataAssetUrl;

@RestController
@RequestMapping(dataAssetUrl)
public class DataAssetController extends BaseController{

    private final Logger LOG = LoggerFactory.getLogger(getClass());
    public static final  String dataAssetUrl = "/assets" ;
    private static final String findByNameAndValueUrl = "/name/{name}/value/{value}";

    @Autowired
    private DataAssetService dataAssetService;

    @RequestMapping(value = findByNameAndValueUrl,
            method = RequestMethod.GET)
    public DataAsset get(@PathVariable String name,  @PathVariable String value) {
        return  dataAssetService.getDataAsset(name, value);
    }

    @RequestMapping(method = RequestMethod.GET)
    public List<DataAsset> getAllDataAsset( ) {
        return dataAssetService.getAll();
    }

}
