import express from "express";
import fetch from "node-fetch";

const app = express();

app.get("/stooq", async (req, res) => {

  try {

    const symbol = req.query.symbol;

    if (!symbol) {
      return res.status(400).send("symbol required");
    }

    const url =
      `https://stooq.com/q/d/l/?s=${symbol}&i=d`;

    const r = await fetch(url, {
      headers: {
        "User-Agent": "Mozilla/5.0"
      }
    });

    const text = await r.text();

    res.set("Content-Type", "text/plain");
    res.send(text);

  } catch (e) {

    res.status(500).send(String(e));

  }

});

const port = process.env.PORT || 3000;

app.listen(port, () => {
  console.log("stooq proxy running");
});
