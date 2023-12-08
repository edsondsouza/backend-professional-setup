# Practicing the folder structure for backend

## One of the way to connect to the database
- This code is written in the index.js file (NOT A BETTER APROACH)
```javascript
import mongoose from "mongoose";
import {DB_NAME} from "./constants.js"

import express from "express";
const app = express()

(async () => {
    try {
        await mongoose.connect(`${process.env.MONGODB_URI}/${DB_NAME}`)
        app.on("error", (error) => {
            console.log("ERROR", error)
            throw error
        })

        app.listen(process.env.PORT, () => {
            console.log(`app is listening on port ${process.env.PORT}`)
        })

    } catch (error) {
        console.error("ERROR: ", error)
        throw error
    }
})();
```