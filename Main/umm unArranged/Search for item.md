```
import React, { useState } from "react";

import axios from "axios";

import { defaultComponents } from "react-select/dist/declarations/src/components";

  

interface Nutrition {

  energy?: number;

  protein?: number;

  fat?: number;

  saturatedFat?: number;

  carbohydrate?: number;

  sugars?: number;

  dietaryFibre?: number;

  sodium?: number;

  potassium?: number;

  transFat?: number;

  polyunsaturatedFat?: number;

  monounsaturatedFat?: number;

  calcium?: number;

  vitaminE?: number;

  vitaminB3?: number;

  magnesium?: number;

  vitaminB1?: number;

  vitaminB2?: number;

  vitaminB6?: number;

  vitaminB9?: number;

  vitaminC?: number;

  iron?: number;

  phosphorus?: number;

  zinc?: number;

  manganese?: number;

  vitaminK?: number;

  vitaminA?: number;

  starch?: number;

  omega3FattyAcid?: number;

}

  

interface Food {

  id: string;

  name: string;

  "nutrition-per-100g"?: Nutrition;

  "nutrition-per-100ml"?: Nutrition;

  tags?: string[];

}

  

const Search: React.FC = () => {

  const [query, setQuery] = useState<string>("");

  const [suggestions, setSuggestions] = useState<string[]>([]);

  const [foodDetails, setFoodDetails] = useState<Food | null>(null);

  const [error, setError] = useState<string>("");

  

  const fetchSuggestions = async (query: string) => {

    try {

      const response = await axios.get<string[]>(

        `http://localhost:5000/api/foods/suggestions?query=${query}`

      );

      setSuggestions(response.data);

    } catch (err) {

      setError("Failed to fetch suggestions");

    }

  };

  

  const fetchFoodDetails = async (name: string) => {

    try {

      const response = await axios.get<Food>(

        `http://localhost:5000/api/foods?name=${name}`

      );

      setFoodDetails(response.data);

      setError("");

    } catch (err) {

      setError("Food not found");

      setFoodDetails(null);

    }

  };

  

  const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>) => {

    const value = e.target.value;

    setQuery(value);

    if (value.length > 2) {

      fetchSuggestions(value);

    } else {

      setSuggestions([]);

    }

  };

  

  const handleSubmit = (e: React.FormEvent) => {

    e.preventDefault();

    fetchFoodDetails(query);

  };

  

  const renderNutrition = (nutrition: Nutrition) => {

    return Object.entries(nutrition).map(([key, value]) => (

      <div key={key} className="mb-2">

        <span className="font-semibold">{key.replace(/([A-Z])/g, ' $1')}: </span>

        <span>{value ?? "N/A"}</span>

      </div>

    ));

  };

  

  return (

    <div className="min-h-screen bg-gray-100 p-6">

      <div className="max-w-2xl mx-auto bg-white rounded-lg shadow-lg p-6">

        <h1 className="text-3xl font-bold text-center text-gray-800 mb-6">Search for Food</h1>

  

        <form onSubmit={handleSubmit} className="flex gap-2 mb-4">

          <input

            type="text"

            value={query}

            onChange={handleInputChange}

            placeholder="Enter food name"

            className="flex-1 p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"

          />

          <button

            type="submit"

            className="p-3 bg-blue-500 text-white rounded-lg hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500"

          >

            Search

          </button>

        </form>

  

        {suggestions.length > 0 && (

          <ul className="bg-white border border-gray-300 rounded-lg shadow-md">

            {suggestions.map((suggestion, index) => (

              <li

                key={index}

                onClick={() => fetchFoodDetails(suggestion)}

                className="p-3 hover:bg-gray-100 cursor-pointer"

              >

                {suggestion}

              </li>

            ))}

          </ul>

        )}

  

        {foodDetails && (

          <div className="mt-6">

            <h2 className="text-2xl font-semibold text-gray-800 mb-4">{foodDetails.name}</h2>

  

            {foodDetails["nutrition-per-100g"] && (

              <div className="mb-6">

                <h3 className="text-xl font-semibold text-gray-700 mb-2">Nutrition per 100g</h3>

                {renderNutrition(foodDetails["nutrition-per-100g"])}

              </div>

            )}

  

            {foodDetails["nutrition-per-100ml"] && (

              <div className="mb-6">

                <h3 className="text-xl font-semibold text-gray-700 mb-2">Nutrition per 100ml</h3>

                {renderNutrition(foodDetails["nutrition-per-100ml"])}

              </div>

            )}

          </div>

        )}

  

        {error && <p className="mt-4 text-center text-red-500 font-semibold">{error}</p>}

      </div>

    </div>

  );

};

  

export default Search;
`````


<div className="min-h-screen p-6 flex flex-col justify-start items-center">

        {/* Large Heading with Small Description */}

        <div className="content mb-8">

          <h1 className="text-4xl font-extrabold text-center text-gray-900 mb-2">

            Welcome to the Nutrition Finder Page

          </h1>

          <p className="text-lg text-center text-gray-600 max-w-3xl mx-auto">

            Find detailed nutritional information for your favorite food items

            and track your health goals easily. Simply type the food name and

            explore the nutritional breakdown.

          </p>

        </div>
 </div>