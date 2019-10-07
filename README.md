package com.place.place.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;

import com.place.place.model.Place;
import com.place.place.service.PlaceService;

@RestController
@RequestMapping("/api")
public class PlaceController {
	
	@Autowired
	PlaceService placeSevice;
	
	@RequestMapping(value="/", method = RequestMethod.GET, produces = "application/json")
	public ResponseEntity<?> findAll() {
		
		ResponseEntity<?> resp = new ResponseEntity<>(HttpStatus.OK);
		resp = placeSevice.findAll();
		return resp;
	}
	
	@RequestMapping(value="/save", method = RequestMethod.POST, produces = "application/json", consumes = "application/json")
	public ResponseEntity<?> save(@RequestBody Place place) {
		ResponseEntity<?> resp = new ResponseEntity<>(HttpStatus.CREATED);
		resp = placeSevice.save(place);
		return resp;
	}
	
	@RequestMapping(value="/update", method = RequestMethod.PUT, produces = "application/json", consumes = "application/json")
	public ResponseEntity<?> update(@RequestBody Place place) {
		ResponseEntity<?> resp = new ResponseEntity<>(HttpStatus.OK);
		resp = placeSevice.update(place);
		return resp;
	}
	
}
