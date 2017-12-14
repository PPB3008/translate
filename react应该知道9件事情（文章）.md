## 好文章收藏  ##

[原文链接](https://camjackson.net/post/9-things-every-reactjs-beginner-should-know?utm_source=qq&utm_medium=social)

### 感受  ###

1. 组件化思想和封装，最开始学习react就很喜欢，但是还是拆分不够明确，导致阅读性差
例如我学习react边想要完成我的毕设，一个音乐在线平台，以下是新碟上架的页面，图片加文字，其实可以在拆分的

```
    class NewAblum extends Component {
  render() {
    let newSongs=null;
    newSongs=newSong.map((newSong) => {
       return <li key={newSong.id} className="song-list">
       <Link to={`datails/${newSong.id}`}>
          <div className="card">
            <div className="card-image">
              <img alt="example" width="100%" src={newSong.picUrl} />
            </div>
            <div  className="card-body">
              <h3>{newSong.name}</h3>
              <p>{newSong.artist.name}</p>
              <p>{newSong.size} song</p>
            </div>
          </div>
          </Link>
        </li>
    });
      return (
        <div className="content-layout">
          <h2>新碟上架</h2>
          <ul className="card-row">{newSongs}</ul>
        </div>
      )
    }
}

```

文章例子


```
    class LatestPostsComponent extends React.Component {
  render() {
    const postPreviews = renderPostPreviews();

    return (
      <section>
        <div><h1>Latest posts</h1></div>
        <div>
          { postPreviews }
        </div>
      </section>
    );
  }

  renderPostPreviews() {
    return this.props.posts.map(post => this.renderPostPreview(post));
  }

  renderPostPreview(post) {
    return (
      <article>
        <h3><a href={`/post/${post.slug}`}>{post.title}</a></h3>
        <time pubdate><em>{post.posted}</em></time>
        <div>
          <span>{post.blurb}</span>
          <a href={`/post/${post.slug}`}>Read more...</a>
        </div>
      </article>
    );
  }
}
```

