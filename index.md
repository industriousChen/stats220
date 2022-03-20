library(magick)

url <- "https://static.boredpanda.com/blog/wp-content/uploads/2015/09/Happy-Cats__880.jpg"
meme <- image_read(url) %>%
  image_scale(300) %>%
      image_annotate(text = "Lazy Cat",
                     color = "#999999",
                     size = 25,
                     font = "Impact",
                     gravity = "north")
ds_text <- image_blank(width = 225, 
                       height = 225, 
                       color = "#999999") %>%
  image_annotate(text = "Lazy\nCat",
                 color = "#ffffff",
                 size = 25,
                 font = "Impact",
                 gravity = "center")
meme <- c(meme, ds_text) %>%
  image_append()
c(meme) %>%
  image_append(stack = TRUE)
image_write(meme, "my_meme.png")
