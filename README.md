# Go Transmission
Golang lib for Transmission API

### Installation

    $ go get github.com/machsix/transmission

### Usage
```go
package main

import (
	"log"
	"./transmission"
)

func main() {
	Client,_ := transmission.New("http://localhost:9092/transmission/rpc", "foo", "bar")

	torrents, err := Client.GetTorrents()
	if err != nil {
		log.Panic(err)
	}

	for _, torrent := range torrents {
		log.Println("Torrent:")
		log.Println("   ID:            ", torrent.ID)
		log.Println("   Name:          ", torrent.Name)
		log.Println("   Status:        ", torrent.Status)
		log.Println("   LeftUntilDone: ", torrent.LeftUntilDone)
		log.Println("   Eta:           ", torrent.Eta)
		log.Println("   UploadRatio:   ", torrent.UploadRatio)
		log.Println("   RateDownload:  ", torrent.RateDownload)
		log.Println("   RateUpload:    ", torrent.RateUpload)
		log.Println("   DownloadDir:   ", torrent.DownloadDir)
		log.Println("   IsFinished:    ", torrent.IsFinished)
		log.Println("   PercentDone:   ", torrent.PercentDone)
		log.Println("   SeedRatioMode: ", torrent.SeedRatioMode)
	}

	url := "magnet:?xt=urn:btih:547fbd07ff0d6888902a7382184fa194975c5bef"
	cmd := transmission.NewAddCmdByURL(url)

  torrent, err := Client.ExecuteAddCommand(cmd)
	log.Println(err)
	log.Printf("%+v",torrent)
}
```

### Original author
Long Nguyen (https://github.com/longnguyen11288/go-transmission)
